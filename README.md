# Leetcode_Prblm_997
class Solution {
public:
    int findJudge(int n, vector<vector<int>>& trust) {
    vector<int> trustCount(n + 1, 0); // Array to count how many people each person trusts
    vector<int> trustedCount(n + 1, 0); // Array to count how many people trust each person
    
    // Count trust relationships
    for (const auto& relation : trust) {
        int a = relation[0];
        int b = relation[1];
        trustCount[a]++;
        trustedCount[b]++;
    }
    
    // Check if there's a person trusted by all others and trusts nobody
    for (int i = 1; i <= n; ++i) {
        if (trustCount[i] == 0 && trustedCount[i] == n - 1) {
            return i;
        }
    }
    
    return -1; // No town judge found
}
        
};
