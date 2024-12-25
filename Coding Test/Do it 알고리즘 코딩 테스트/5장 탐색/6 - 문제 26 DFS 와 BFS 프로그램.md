




```java
public class App {

    static ArrayList<Integer>[] G;
    static boolean[] visited;
    static StringBuilder sb;

    public static void main(String[] args) throws Exception {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        StringTokenizer st = new StringTokenizer(br.readLine());
        sb = new StringBuilder();

        int n = Integer.parseInt(st.nextToken());
        int edges = Integer.parseInt(st.nextToken());
        int start  = Integer.parseInt(st.nextToken());

        G = new ArrayList[n+1];
        for (int i=1; i<n+1; i++) {
            G[i] = new ArrayList<>();
        }

        // 인풋 값에 따라, 서로 연결된 노드를 저장
        // G 자체가 그래프였음을 이제야 깨달음
        for (int i=0; i<edges; i++) {
            st = new StringTokenizer(br.readLine());
            int s = Integer.parseInt(st.nextToken());
            int e = Integer.parseInt(st.nextToken());
            
            G[s].add(e);
            G[e].add(s);
        }

        // 문제 조건에서 연결된 노드 중 번호가 작은 것부터 방문하기 때문에 정렬
        for (int i=1; i<n+1; i++) {
            Collections.sort(G[i]);
        }

        visited = new boolean[n+1];
        DFS(start);
        sb.append("\n");
        // 방문 배열 초기화
        visited = new boolean[n+1];
        BFS(start);

        bw.write(sb.toString());
        bw.newLine();
        bw.flush();
        bw.close();
    }

    static public void DFS (int start){
        if (visited[start]) return;
        visited[start] = true;
        sb.append(start).append(" ");
        
        // 연결된 노드를 순회하며 방문하지 않은 노드를 방문
        // Recursive function -> stack 과 같은 특성을 가짐
        // 이미 작은 원소순으로 정렬된 G[start]
        for (int x : G[start]) {
            if (!visited[x]) {
                DFS(x);
            }
        }
    }

    // BFS 는 큐를 사용 - recursive 하지 않음
    static public void BFS (int start) {
        Queue<Integer> queue = new LinkedList<>();

        queue.add(start);
        // 큐가 빌 때 까지
        while(!queue.isEmpty()) {

            // 현재 노드를 정의할 수 있음
            int current = queue.peek();

            // 현재 노드에 대해서 계산할 수 있음
            // queue 의 첫번째 원소가 방문하지 않았다면 해당 노드에 대해서 검색
            if (!visited[current]) {
                // 만약 현재 노드가 방문했다면
                visited[current] = true;
                sb.append(current).append(" ");
                
                // BFS 는 Queue 를 사용한다. 왜냐하면 인접한 노드들을 큐에 추가하고, 또 큐에서
                // pop 하기 때문이다. 이렇게 되면 탐색하고자 하는 노드에 인접한 원소들을 먼저 조회하게 된다.
                for (int i : G[current]) {
                    queue.add(i);
                }
            }
            queue.remove();
        }
    }

}


```

일단 여기서 나와있는 문제는
모든 노드가 그래프로 인해 탐색 될 수 있음을 가정으로 한다.


DFS 을 recursion 이 아니라 stack 을 이용해서 풀 수 있다.

```java

public class App {

    static StringTokenizer st;
    static StringBuilder sb;
    static ArrayList<Integer>[] G;
    static boolean[] visited;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        sb = new StringBuilder();
        st = new StringTokenizer(br.readLine());

        int n = Integer.parseInt(st.nextToken());
        int edges = Integer.parseInt(st.nextToken());
        int start = Integer.parseInt(st.nextToken());

        G = new ArrayList[n+1];
        for (int i=1; i<=n; i++) {
            G[i] = new ArrayList<>(); }

        for (int i=0; i<edges; i++) {
            st = new StringTokenizer(br.readLine());
            int s = Integer.parseInt(st.nextToken());
            int e = Integer.parseInt(st.nextToken());

            G[s].add(e);
            G[e].add(s);
        }

        visited = new boolean[n+1]; // 1-indexed
        // 작은 수부터 참조 되려면 각 array 가 내림차순 정렬되어야 한다. 
        // 그래야 앞에서부터 들어갈때 가장 먼저 조회되는 것이 가장 작은 수가 됨
        for (int i=1; i<=n; i++) {
            G[i].sort(((o1, o2) -> o2 - o1));
        }
        DFS(start);

        visited = new boolean[n+1];
        for (int i=1; i<=n; i++) {
            Collections.sort(G[i]);
        }
        sb.append("\n");
        BFS(start);

        bw.write(sb.toString());
        bw.newLine();
        bw.flush();
        bw.close();
    }

    public static void DFS (int start) {
        Stack<Integer> stack = new Stack<>();
        stack.push(start);

        while (!stack.isEmpty()) {
            int current = stack.pop();
            if (!visited[current]) {
                visited[current] = true;
                sb.append(current).append(" ");
                for (int point : G[current]) {
                    stack.push(point);
                }
            }
        }
    }

    public static void BFS (int start) {
        Queue<Integer> q = new LinkedList<>();
        q.add(start);

        while (!q.isEmpty()) {
            int current = q.poll();
            if (!visited[current]) {
                visited[current] = true;
                sb.append(current).append(" ");

                q.addAll(G[current]);
            }
        }
    }
}

```