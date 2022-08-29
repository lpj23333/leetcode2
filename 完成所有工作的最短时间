bool backtrack(int* jobs, int jobsSize, int* workloads, int workloadsSize, int idx, int limit) {
    if (idx >= jobsSize) {
        return true;
    }
    int cur = jobs[idx];
    for (int i = 0; i < workloadsSize; i++) {
        if (workloads[i] + cur <= limit) {
            workloads[i] += cur;
            if (backtrack(jobs, jobsSize, workloads, workloadsSize, idx + 1, limit)) {
                return true;
            }
            workloads[i] -= cur;
        }
        // 如果当前工人未被分配工作，那么下一个工人也必然未被分配工作
        // 或者当前工作恰能使该工人的工作量达到了上限
        // 这两种情况下我们无需尝试继续分配工作
        if (workloads[i] == 0 || workloads[i] + cur == limit) {
            break;
        }
    }
    return false;
}

bool check(int* jobs, int jobsSize, int k, int limit) {
    int workloads[k];
    memset(workloads, 0, sizeof(workloads));
    return backtrack(jobs, jobsSize, workloads, k, 0, limit);
}

int cmp(int* a, int* b) {
    return *b - *a;
}

int accumulate(int* arr, int* arrSize) {
    int ret = 0;
    for (int i = 0; i < arrSize; i++) {
        ret += arr[i];
    }
    return ret;
}

int minimumTimeRequired(int* jobs, int jobsSize, int k) {
    qsort(jobs, jobsSize, sizeof(int), cmp);
    int l = jobs[0], r = accumulate(jobs, jobsSize);
    while (l < r) {
        int mid = (l + r) >> 1;
        if (check(jobs, jobsSize, k, mid)) {
            r = mid;
        } else {
            l = mid + 1;
        }
    }
    return l;
}
