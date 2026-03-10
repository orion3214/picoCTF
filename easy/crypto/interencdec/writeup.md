# You got the file

The file contained:

```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzVNR3N5TXpjNWZRPT0nCg==
```

This is **Base64-encoded data** (you could tell because of `=` padding at the end).

------

# Decode Base64 once

Using **CyberChef** (or dcode.fr) → **“From Base64”** gave:

```
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ=='
```

Notice this is **still Base64** (the output still ends with `=`), just one layer decoded. This is very common in CTFs — sometimes flags are **double Base64 encoded** to make you think.

------

# Decode Base64 a second time

Take:

```
d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ==
```

Use **“From Base64”** again → now you get the **actual flag**:

```
wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}
```

 That’s the **picoCTF flag format**: `picoCTF{...}` or similar (here they used `wpjvJAM{...}`).

------

# Tools used

- **dcode.fr**: Great for base64, hex, URL encoding, and classical ciphers.
- **CyberChef**: Another universal decoding/encoding tool.

Both allowed you to **decode layer by layer** without writing any code.
