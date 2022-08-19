# history-sequence
The first line gives the number of events, n, and the number of known events, k, in the first line. The next k lines are given the numbers of the two events of known context. This means that the event in the preceding number occurred before the event in the number after it. Of course, there is no case where the context of the event is contradictory. Next, we are given the number s of pairs of events for which we want to know the context of an event. The next s line is given the number of two different events, respectively. The number of events is a natural number greater than or equal to 1 and less than or equal to n. Answer the questions across s lines. On each line, print -1 if the preceding numbered event occurred first, 1 if the second numbered event occurred first, or 0 if you do not know what! 첫째 줄에 첫 줄에 사건의 개수 n과 알고 있는 사건의 전후 관계의 개수 k가 주어진다. 다음 k줄에는 전후 관계를 알고 있는 두 사건의 번호가 주어진다. 이는 앞에 있는 번호의 사건이 뒤에 있는 번호의 사건보다 먼저 일어났음을 의미한다. 물론 사건의 전후 관계가 모순인 경우는 없다. 다음에는 사건의 전후 관계를 알고 싶은 사건 쌍의 수 s가 주어진다. 다음 s줄에는 각각 서로 다른 두 사건의 번호가 주어진다. 사건의 번호는 1보다 크거나 같고, n보다 작거나 같은 자연수이다. s줄에 걸쳐 물음에 답한다. 각 줄에 만일 앞에 있는 번호의 사건이 먼저 일어났으면 -1, 뒤에 있는 번호의 사건이 먼저 일어났으면 1, 어떤지 모르면 0을 출력해라!
