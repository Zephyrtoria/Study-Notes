# ACM模式

# 输入

## 小规模 Scanner

‍

## 大规模 BufferedReader

注意抛出异常

```Java
public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    String[] input = br.readLine().split(" ");
    int n, m;
    n = Integer.parseInt(input[0]);
    m = Integer.parseInt(input[1]);

    input = br.readLine().split(" ");
    for (int i = 1; i <= n; i++) {
        r[i] = Long.parseLong(input[i - 1]);
    }

    for (int i = 1; i <= m; i++) {
        input = br.readLine().split(" ");
        d[i] = Integer.parseInt(input[0]);
        s[i] = Integer.parseInt(input[1]);
        t[i] = Integer.parseInt(input[2]);
    }
}
```
