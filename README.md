- 👋 Hi, I’m @ryomamoyr
```Python
def manacher(s: str) -> str:
    t = "^#" + "#".join(s) + "#$"
    n = len(t)

    p = [0] * n
    center = right = 0

    for i in range(1, n - 1):
        mirror = 2 * center - i

        if i < right:
            p[i] = min(right - i, p[mirror])

        while t[i + p[i] + 1] == t[i - p[i] - 1]:
            p[i] += 1

        if i + p[i] > right:
            center = i
            right = i + p[i]

    max_length = max(p)
    center_index = p.index(max_length)

    start = (center_index - max_length) // 2
    return s[start : start + max_length]

```
<!---
ryomamoyr/ryomamoyr is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
