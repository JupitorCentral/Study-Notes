


repeat from 0 to n-1-(length of password)

extract string using index : i to i + length
check all characters and save frequencies of each characaters.

주의해야 할 것은 $O(N^2)$ 이 되면 안된다.
그러니까 포인트를 2개 두어서 포인트를 옮길때마다 현재 문자열에 해당하는 캐릭터들의 상황을 업데이트 해주어야 한다.

처음 length 만큼 characters 에 add
그 다음 하나씩 옮겨가면서 add & slide 에 벗어난 부분 sub
그 다음 판단


``` java
public class App {

    static StringBuilder sb;
    static int [] characters;
    static int [] goals;

    public static void main(String[] args) throws Exception {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        StringTokenizer st = new StringTokenizer(br.readLine());
        sb = new StringBuilder();

        int n = Integer.parseInt(st.nextToken());
        int length = Integer.parseInt(st.nextToken());

        char[] arr = br.readLine().toCharArray();

        characters = new int[4];
        goals = new int[4];

        st = new StringTokenizer(br.readLine());
        for (int i=0; i<4; i++) { goals[i] = Integer.parseInt(st.nextToken()); }

        int count = 0;
        // 처음 window 
        for (int i=0; i<length; i++) {
            updateCharacters(true, arr[i]);
        }
        if (check()) count++;


        for (int i=length; i<n; i++) {
            updateCharacters(true, arr[i]);
            updateCharacters(false, arr[i-length]);

            // check
            if (check()) count++;
        }

        sb.append(Integer.toString(count));

        bw.write(sb.toString());
        bw.newLine();
        bw.flush();
        bw.close();
    }

    // if mode is true, it's addition
    public static void updateCharacters (boolean mod, char character) {
        int target = 0;
        
        switch (character) {
            case 'A' -> target = 0;
            case 'C' -> target = 1;
            case 'G' -> target = 2;
            case 'T' -> target = 3;
        }

        if (mod) characters[target]++;
        else characters[target]--;
    }

    public static boolean check () {
        return characters[0] >= goals[0] && characters[1] >= goals[1] && characters[2] >= goals[2] && characters[3] >= goals[3];
    }
}
```
