/* The summary of interview questions. */

1. 经典的小偷问题：一排房子，每个房子里有一定价值的东西，小偷不能偷相邻的两
个房间。即如果小偷光临了房间i, 那么就不能再偷房间i - 1和房间i + 1。要求返回
小偷能偷到东西的总价值的最大值。这是个经典DP问题，版上讨论过。
Sol: Suppose v[i] = the value of house i, and totally we have n houses.
f[0] = v[0], f[1] = v[1], f[i] = max{f[i - 1], f[i - 2] + v[i]} for i >= 2

A modified version of this problem is that all houses form a circle, whose 
solution is very similar. We need to run DP twice.
1st: f[0] = v[0], f[1] = 0, f[i] = max{f[i - 1], f[i - 2] + v[i]} for i = 2,
3, ..., n - 2 ==> ans1 = f[n - 2]
2nd: f[0] = 0, f[1] = v[1], f[i] = max{f[i - 1], f[i - 2] + v[i]} for i = 2,
3, ..., n - 1 ==> ans2 = f[n - 1]
return max{ans1, ans2}
