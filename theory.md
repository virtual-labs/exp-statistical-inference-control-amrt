
Statistical databases provide access to data through **aggregate queries** such as `COUNT`, `SUM`, and `AVERAGE`, which are designed to protect individual privacy by returning only summarized results. However, even when direct access to individual records is restricted, **sensitive information can still be inferred** through carefully constructed query patterns. As a result, statistical databases are vulnerable to **inference attacks**, where attackers exploit aggregate query outputs to deduce private individual data.

One of the most common inference techniques is the **differencing attack**, in which an attacker executes multiple aggregate queries with slightly different conditions and compares their results. By analyzing the difference between query outputs, the attacker can infer information about a specific individual or a very small group. Repeated execution of such queries can gradually lead to significant data leakage.

To mitigate these risks, the simulation demonstrates the following **defense mechanisms**:


#### 1. Noise Addition

Noise Addition protects sensitive information by adding a small, controlled random value to aggregate query results. This prevents attackers from obtaining exact values, even when the same query is executed multiple times. While overall statistical trends remain useful, precise inference of individual records becomes unreliable.



#### 2. k-Anonymity (Query-Set-Size Control)

k-Anonymity ensures that aggregate query results are returned only when the number of records involved in the query is greater than or equal to a predefined threshold **k**. If the query result set size is smaller than **k**, the system suppresses or blocks the output, preventing attackers from isolating individual records or very small groups.



#### 3. Rate Limiting

Rate Limiting restricts the number of queries a user can execute within a specified time window. Since inference attacks rely on repeatedly issuing similar or related queries, limiting query frequency significantly reduces the attacker’s ability to collect enough information to infer private data.


#### 4. Differencing Protection

Differencing Protection detects and blocks query patterns that attempt to infer private information by comparing results of closely related queries, such as queries that differ only by the inclusion or exclusion of a single record. By identifying and preventing such complementary queries, the system directly mitigates differencing attacks.



