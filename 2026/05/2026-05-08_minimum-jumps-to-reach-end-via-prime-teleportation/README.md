# Minimum Jumps to Reach End via Prime Teleportation

**Date:** 2026-05-08  
**Difficulty:** 🟡 **Medium**  
**Tags:** `Array` `Hash Table` `Math` `Breadth-First Search` `Number Theory`

## Problem Description

You are given an integer array nums of length n . You start at index 0, and your goal is to reach index n - 1 . From any index i , you may perform one of the following operations: Adjacent Step : Jump to index i + 1 or i - 1 , if the index is within bounds. Prime Teleportation : If nums[i] is a prime number p , you may instantly jump to any index j != i such that nums[j] % p == 0 . Return the minimum number of jumps required to reach index n - 1 . Example 1: Input: nums = [1,2,4,6] Output: 2 Explanation: One optimal sequence of jumps is: Start at index i = 0 . Take an adjacent step to index 1.

[LeetCode Link](https://leetcode.com/problems/minimum-jumps-to-reach-end-via-prime-teleportation)

## Approach

BFS with Prime Teleportation via Smallest Prime Factor Sieve

> Use BFS on index graph where edges include adjacent steps and prime-grouped teleportations, marking used prime channels to avoid redundant traversal.

## Solution Logic

1. Step 1: Build a Smallest Prime Factor (SPF) sieve up to MAXV to efficiently factorize numbers and check primality in O(log n).
2. Step 2: Scan nums to record which prime values actually appear (primeSeen), then build a map from each such prime p to all indices whose value is divisible by p — these are the teleportation targets.
3. Step 3: Run BFS from index 0. For each index dequeued, enqueue adjacent indices (i-1, i+1) if unvisited. If nums[i] is a prime p not yet used as a teleport channel, mark p as used and enqueue all indices in mp[p] that are unvisited, all at cost dist[i]+1.
4. Step 4: The 'usedPrime' flag is critical: once a prime channel is fully expanded in BFS, it never needs to be expanded again, preventing O(n^2) blowup from repeated teleportation processing.
5. Step 5: Return dist[n-1] when the destination is first reached, or -1 if unreachable.

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(MAXV + n * log(maxVal)) — SPF sieve is O(MAXV log log MAXV), factorization per element is O(log maxVal), BFS visits each index and each prime channel at most once so total teleportation work is O(n). |
| **Space:** | O(MAXV + n) — SPF sieve is O(MAXV), prime-to-indices map holds O(n) total entries, dist and usedPrime arrays are O(n) and O(MAXV) respectively. |

## Edge Cases Handled

- Single element array (n=1, return 0 immediately)
- Values equal to 1 (skipped in factorization, no teleportation)
- Duplicate prime factors in a number (inner while loop divides out all copies)
- Primes in nums that have no multiples elsewhere (primeSeen filter avoids useless map entries)
- Reusing the same prime teleport channel multiple times (usedPrime flag prevents redundant BFS expansion)

## What I Learned

When multiple nodes share a property (divisible by prime p), treat the prime as a virtual BFS channel: expand it once and mark it consumed, reducing what could be O(n^2) teleportation edges to O(n) total work — the same 'virtual node' trick used in problems like Jump Game IV.

## Similar Problems

- Jump Game IV (LeetCode 1345)
- Jump Game VII (LeetCode 1871)
- Minimum Jumps to Reach Home (LeetCode 1654)
- Word Ladder (LeetCode 127)
- Open the Lock (LeetCode 752)

## Solution Code

```text
class Solution {
public:
    static constexpr int MAXV = 1'000'001;

    // smallest prime factor sieve
    static const vector<int>& getSPF() {

        static const vector<int> spf = [](){
            vector<int> s(MAXV);
            for(int i = 0; i < MAXV; i++){
                s[i] = i;
            }

            s[0] = 0;
            s[1] = 1;
            for(long long i = 2; i * i < MAXV; i++){
                if(s[i] == i){

                    for(long long j = i * i; j < MAXV; j += i){
                        if(s[j] == j){
                            s[j] = i;
                        }
                    }
                }
            }
            return s;
        }();
        return spf;
    }

    bool isPrime(int x, const vector<int>& spf){

        return x >= 2 && spf[x] == x;
    }

    int minJumps(vector<int>& nums) {

        int n = nums.size();

        if(n == 1) return 0;

        const auto& spf = getSPF();

        int maxi = *max_element(nums.begin(), nums.end());

        // store which prime numbers are present in nums
        vector<char> primeSeen(maxi + 1, false);

        for(int x : nums){

            if(isPrime(x, spf)){
                primeSeen[x] = true;
            }
        }

        // prime -> indices divisible by that prime
        unordered_map<int, vector<int>> mp;
        mp.reserve(n * 2);

        for(int i = 0; i < n; i++){

            int x = nums[i];

            if(x == 1) continue;

            while(x > 1){

                int p = spf[x];

                // only store useful primes
                if(p <= maxi && primeSeen[p]){
                    mp[p].push_back(i);
                }

                // remove duplicate prime factors
                while(x % p == 0){
                    x /= p;
                }
            }
        }

        vector<int> dist(n, -1);

        // to avoid reusing same teleportation
        vector<char> usedPrime(maxi + 1, false);

        queue<int> q;

        q.push(0);
        dist[0] = 0;

        while(!q.empty()){

            int idx = q.front();
            q.pop();

            if(idx == n - 1){
                return dist[idx];
            }

            // left move
            if(idx - 1 >= 0 && dist[idx - 1] == -1){

                dist[idx - 1] = dist[idx] + 1;
                q.push(idx - 1);
            }

            // right move
            if(idx + 1 < n && dist[idx + 1] == -1){
                dist[idx + 1] = dist[idx] + 1;
                q.push(idx + 1);
            }

            int x = nums[idx];
            // teleportation
            if(x <= maxi && isPrime(x, spf) && !usedPrime[x]){
                usedPrime[x] = true;
                auto it = mp.find(x);
                if(it != mp.end()){

                    for(int nextIdx : it->second){
                        if(dist[nextIdx] == -1){

                            dist[nextIdx] = dist[idx] + 1;
                            q.push(nextIdx);
                        }
                    }
                }
            }
        }

        return -1;
    }
};
```
