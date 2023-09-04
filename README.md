# Thu-t-to-n-Bellman---Ford
Xét trường hợp đơn giản hơn, khi đồ thị không có trọng số âm (tức đường đi ngắn nhất luôn tồn tại).  Thuật toán Bellman-Ford sẽ lặp nhiều lần. Ở mỗi vòng lặp, ta sẽ đi qua tất cả các cạnh (u,v)  trên đồ thị, so sánh đường đi S→v  đã tìm được với đường đi S→u→v
const long long INF = 2000000000000000000LL;
struct Edge {
    int u, v;
    long long w; // cạnh từ u đến v, trọng số w
};
void bellmanFord(int n, int S, vector<Edge> &e, vector<long long> &D, vector<int> &trace) {
    // e: danh sách cạnh
    // n: số đỉnh
    // S: đỉnh bắt đầu
    // D: độ dài đường đi ngắn nhất
    // trace: mảng truy vết đường đi
    // INF nếu không có đường đi
    // -INF nếu có đường đi âm vô tận
    D.resize(n, INF);
    trace.resize(n, -1);

    D[S] = 0;
    for(int T = 1; T < n; T++) {
        for (auto E : e) {
            int u = E.u;
            int v = E.v;
            long long w = E.w;
            if (D[u] != INF && D[v] > D[u] + w) {
                D[v] = D[u] + w;
                trace[v] = u;
            }
        }
    }
}
