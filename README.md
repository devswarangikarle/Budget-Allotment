# Budget-Allotment

This year's annual budget involved a discussion on N sectors where the ith sector was initially allocated an amount Ai​.
It was later realised that a minimum budget of X is required by each sector. Allocation can be transferred from sector i to any sector j only if the final allocation for sector i remains at least X.
Find the maximum number of sectors that can meet the minimum required budget of X after possible transfers?

def max_funded_sectors(N, X, A):
    A.sort(reverse=True)  
    total_budget = 0
    sectors_funded = 0
    
    for i in range(N):
        total_budget += A[i]  
        if total_budget >= (sectors_funded + 1) * X:  
            sectors_funded += 1
        else:
            break  

    return sectors_funded

T = int(input())

results = []

for _ in range(T):
    N, X = map(int, input().split())
    A = list(map(int, input().split()))
    
    results.append(str(max_funded_sectors(N, X, A)))

print("\n".join(results))
