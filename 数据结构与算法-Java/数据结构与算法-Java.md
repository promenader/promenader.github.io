# 数据结构与算法-Java



## 第一篇：数据结构



### 1、数组

```java
import java.util.*;

class Solution {
    public List<Integer> eventualSafeNodes(int[][] graph) {
        List<Integer> result = new ArrayList<>();
        for(int i=0;i< graph.length;i++){
            int[] cur = graph[i];
            if(cur == null || cur.length==0) {
                result.add(i);
                continue;
            }
            if(!hasCircle(graph,i)) {
                result.add(i);
            }
        }
        Collections.sort(result);
        return result;
    }

    public boolean hasCircle(int[][] graph,int start){
        Queue<Integer> queue = new LinkedList<>();
        int v = graph.length;
        int[] color =  new int[v];

        queue.offer(start);
        color[start]=1;
        while (!queue.isEmpty()) {
            int cur = queue.poll();
            for(int next: graph[cur] ){
                if(color[next]==0) {
                    queue.offer(next);
                    color[next]=1;
                } else if (color[next]==1) {
                    return true;
                }
            }
            color[cur]=2;
        }
        return false;
    }
}
```







