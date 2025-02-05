# Marvin

```python
import marvin
import markitdown

mid = markitdown.MarkItDown()

# convert the PDF to plain text
content = mid.convert("Koop et al. - 2012 - Biological Invasions.pdf").text_content

# call LLM to extract keywords
marvin.extract(content, instructions="keywords")
```
