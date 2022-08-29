int cmp(int* a, int* b) {
    return *b - *a;
}

int kthLargestValue(int** matrix, int matrixSize, int* matrixColSize, int k) {
    int m = matrixSize, n = matrixColSize[0];
    int pre[m + 1][n + 1];
    memset(pre, 0, sizeof(pre));
    int results[m * n], resultsSize = 0;
    for (int i = 1; i <= m; ++i) {
        for (int j = 1; j <= n; ++j) {
            pre[i][j] = pre[i - 1][j] ^ pre[i][j - 1] ^ pre[i - 1][j - 1] ^ matrix[i - 1][j - 1];
            results[resultsSize++] = pre[i][j];
        }
    }

    qsort(results, resultsSize, sizeof(int), cmp);
    return results[k - 1];
}
