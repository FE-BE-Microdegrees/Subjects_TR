# Markdown

- [Markdown](#markdown)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Markdown?](#what-is-markdown)
  - [What is a Markup Language?](what-is-a-markup-language?)
  - [Advantages of Markdown:](#advantages-of-markdown)
  - [Disadvantages of Markdown:](#disadvantages-of-markdown)
  - [When to Use Markdown:](#when-to-use-markdown)
  - [Basic Markdown Syntax:](#basic-markdown-syntax)
    - [Headings:](#headings)
    - [Emphasis:](#emphasis)
    - [Lists:](#lists)
      - [Unordered:](#unordered)
      - [Ordered:](#ordered)
    - [Links:](#links)
    - [Images:](#images)
    - [Blockquotes:](#blockquotes)
    - [Inline Code:](#inline-code)
    - [Code Blocks:](#code-blocks)
    - [Horizontal Rule:](#horizontal-rule)
    - [Tables:](#tables)
    - [Task Lists:](#task-lists)
  - [Excercises](#excercises)

## Learning Outcomes

After completing this topic, you'll be able to:

- describe what Markdown is and why it's useful;
- identify the pros and cons of Markdown;
- use Markdown to format text;
- use Markdown for documentation, blogging, and other purposes.
- use Markdown in Github.

## What is Markdown?

Markdown is a lightweight markup language with a simple text formatting syntax. It was created by John Gruber in 2004. The main goal of Markdown was to make it easy for people to write and format text in a way that is freely readable and can be converted to HTML (or other output formats).

## What is a Markup Language?

A markup language is a language used for formatting or structuring text by adding markers or tags. Markers are usually some symbols or combinations of symbols added to the text to define what formatting or structure some text should have. Markup languages are widely used in documentation, web page creation, blogging, and many other contexts.

Common markup languages include:

- HTML
- XML
- LaTeX
- Markdown
- etc.

## Advantages of Markdown:

- **Simplicity:** Markdown is easy to learn and use. Its syntax is intuitive, meaning that even non-technical people can easily start writing in this format.
- **Readability:** Markdown documents consist of plain text, therefore they are readable even without converting to another format.
- **Portability:** Since these are plain text files, Markdown documents are OS-agnostic and can be opened with any text editor.
- **Flexible Output:** Markdown can be converted to a variety of formats, including HTML, PDF, and even MS Word or LaTeX format.
- **Widespread Use:** Many platforms, such as GitHub, Reddit, Stack Exchange, and even messaging applications like Slack and Discord, support Markdown. It is also a popular choice for documentation and blogging.
- **Version Control Friendly:** Being plain text, Markdown works seamlessly with version control systems like Git.
- **No Need for Specialized Software:** Markdown can be written in any text editor. Additionally, there are specialized Markdown editors that offer additional features, such as preview and quick conversion.


## Disadvantages of Markdown:

- **Limited Styling:** While Markdown easily handles basic formatting, it is not suitable for composing documents that require complex styles or layouts.
- **Inconsistencies:** There are several variations of Markdown, and not all tools support every feature. For example, GitHub's Markdown processing may be slightly different from other platforms.
- **Not Ideal for Large Documents:** While Markdown can certainly be used for larger documents, it might not be as manageable or structured as other formats created for this purpose.
- **No Built-in Preview:** Without using a specialized Markdown editor, it is not possible to preview the formatted output without converting it. However, it's possible to install plugins to some editors that enable preview, like VS Code with the Markdown All in One plugin.

## When to Use Markdown

- **Documentation:** Many open-source projects use Markdown for their README files and documentation, as it is simple and GitHub supports it by default.
- **Blogging:** Many blog platforms and static site generators support Markdown, as it is readable and user-friendly.
- **Note-taking:** Markdown is great for taking structured notes. There are several note-taking applications that support Markdown formatting.
- **Online Discussions:** Platforms like Reddit and Stack Exchange use Markdown for formatting text in comments and posts.
- **Writing Books:** Some authors use Markdown for writing books, especially technical books, as it is simple and allows for conversion into various formats.
- **Presentations:** Tools like Reveal.js or Marp allow creating presentations using Markdown.
- **Educational Materials:** Markdown is suitable for creating educational materials, such as tutorials, cheat sheets, and more. This format is easy to write and read, and it can be converted into various formats. If something changes in the source material, you only need to update the Markdown file and regenerate the output.

In summary, Markdown is an excellent choice for projects that require basic formatting without the additional overhead of more complex markup languages. Its simplicity and readability are the main strengths of Markdown, but for more complex layouts or extensive styling, other formats might be more appropriate.

## Basic Markdown Syntax:

Here's a quick reference to basic Markdown syntax:

### Headings:

```markdown
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

### Emphasis:

```markdown
*italic* or _italic_
**bold** or __bold__
**_italic and bold_** or *__italic and bold__*
~~strikethrough~~
```

### Lists:

#### Unordered:

```markdown
* Item 1
* Item 2
  * Subitem 2.1
  * Subitem 2.2
```

or 

```markdown
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2
```

#### Ordered:

```markdown
1. First item
2. Second item
   1. Subitem 2.1
   2. Subitem 2.2
```

### Links:

```markdown
[Google](https://www.google.com)
```

### Images:

```markdown
![Alt text](url_to_image)
```

### Blockquotes:

```markdown
> This is a blockquote.
```

### Inline Code:

```markdown
Here is `inline code`.
```

### Code Blocks:

Using three backticks:

<pre>
```
function example() {
  console.log("example");
}
```
</pre>

Or with syntax highlighting:

<pre>
```javascript
function example() {
  console.log("example");
}
```
</pre>

### Horizontal Rule:

```markdown
---
```

or 

```markdown
***
```

### Tables:

```markdown
| Header 1 | Header 2 |
| -------- | -------- |
| Cell1    | Cell2    |
| Cell3    | Cell4    |
```

### Task Lists:

```markdown
- [x] Task 1 (completed)
- [ ] Task 2 (not completed)
```

Remember, different platforms or flavors of Markdown might have additional features or slight variations, but the above covers the basic and commonly-used syntax.

Read more from [Markdown Guide](https://www.markdownguide.org/).

# Markdown

- [Markdown](#markdown)
  - [Öğrenme Çıktıları](#öğrenme-çıktıları)
  - [Markdown Nedir?](#markdown-nedir)
  - [Biçimleme Dili Nedir?](#biçimleme-dili-nedir)
  - [Markdown'un Avantajları:](#markdownun-avantajları)
  - [Markdown'un Dezavantajları:](#markdownun-dezavantajları)
  - [Markdown Ne Zaman Kullanılır?](#markdown-ne-zaman-kullanılır)
  - [Markdown Temel Sözdizimi:](#markdown-temel-sözdizimi)
    - [Başlıklar:](#başlıklar)
    - [Vurgu:](#vurgu)
    - [Listeler:](#listeler)
      - [Sırasız:](#sırasız)
      - [Sıralı:](#sıralı)
    - [Bağlantılar:](#bağlantılar)
    - [Resimler:](#resimler)
    - [Alıntılar:](#alıntılar)
    - [Satır İçi Kod:](#satır-ici-kod)
    - [Kod Blokları:](#kod-blokları)
    - [Yatay Çizgi:](#yatay-çizgi)
    - [Tablolar:](#tablolar)
    - [Görev Listeleri:](#görev-listeleri)
  - [Alıştırmalar](#alıştırmalar)

## Öğrenme Çıktıları

Bu konuyu tamamladıktan sonra şunları yapabileceksiniz:

- Markdown'un ne olduğunu ve neden faydalı olduğunu açıklayabilirsiniz;
- Markdown'un avantajlarını ve dezavantajlarını tanımlayabilirsiniz;
- Markdown ile metin biçimlendirebilirsiniz;
- Markdown'u dökümantasyon, blog yazımı ve diğer amaçlar için kullanabilirsiniz;
- Markdown'u GitHub üzerinde kullanabilirsiniz.

## Markdown Nedir?

Markdown, basit bir metin biçimlendirme sözdizimine sahip hafif bir biçimleme dilidir. 2004 yılında John Gruber tarafından geliştirilmiştir. Markdown'un temel amacı, insanların HTML (veya diğer çıktı formatlarına) dönüştürülebilecek bir şekilde metin yazmalarını ve biçimlendirmelerini kolaylaştırmaktır.

## Biçimleme Dili Nedir?

Bir biçimleme dili, metni biçimlendirmek veya yapılandırmak için kullanılan bir dildir. Bu diller, metne eklenen işaretler veya etiketlerle, belirli metinlerin nasıl biçimlendirilmesi veya yapılandırılması gerektiğini tanımlar. Biçimleme dilleri dökümantasyon, web sayfası oluşturma, blog yazımı ve daha birçok bağlamda yaygın olarak kullanılır.

Yaygın biçimleme dilleri şunlardır:

- HTML
- XML
- LaTeX
- Markdown
- vb.

## Markdown'un Avantajları:

- **Basitlik:** Markdown öğrenmesi ve kullanması kolaydır. Sözdizimi sezgiseldir ve teknik olmayan kişiler bile kolaylıkla bu formatta yazmaya başlayabilir.
- **Okunabilirlik:** Markdown belgeleri düz metin içerdiğinden, başka bir formata dönüştürülmeden bile okunabilir.
- **Taşınabilirlik:** Bu dosyalar düz metin olduğundan, Markdown belgeleri işletim sistemi bağımsızdır ve herhangi bir metin editörüyle açılabilir.
- **Esnek Çıkış:** Markdown, HTML, PDF ve hatta MS Word veya LaTeX formatı gibi çeşitli formatlara dönüştürülebilir.
- **Yaygın Kullanım:** GitHub, Reddit, Stack Exchange ve hatta Slack, Discord gibi mesajlaşma uygulamaları Markdown'u destekler.
- **Versiyon Kontrol Uyumlu:** Düz metin olduğundan, Markdown versiyon kontrol sistemleriyle (örneğin Git) sorunsuz çalışır.
- **Özel Yazılım Gerekmez:** Markdown herhangi bir metin editöründe yazılabilir.

## Markdown'un Dezavantajları:

- **Sınırlı Stil Seçenekleri:** Markdown temel biçimlendirmeleri kolayca yaparken, karmaşık stiller veya düzen gerektiren belgeler için uygun değildir.
- **Tutarsızlıklar:** Markdown'un birkaç varyasyonu vardır ve tüm araçlar her özelliği desteklemez.
- **Büyük Belgeler İçin İdeal Değil:** Markdown büyük belgeler için kullanılabilir, ancak daha yönetilebilir ve yapısal formatlar kadar uygun olmayabilir.
- **Yerleşik Önizleme Yok:** Özel bir Markdown editörü kullanmadan, formatlanmış çıktıyı dönüştürmeden önizlemek mümkün değildir.

## Markdown Ne Zaman Kullanılır?

- **Dökümantasyon:** Markdown, README dosyaları ve dökümantasyon için sıklıkla kullanılır.
- **Blog Yazımı:** Markdown birçok blog platformu tarafından desteklenir.
- **Not Tutma:** Markdown yapılandırılmış notlar almak için harikadır.
- **Çevrimiçi Tartışmalar:** Reddit ve Stack Exchange gibi platformlar Markdown'u kullanır.
- **Kitap Yazımı:** Markdown kitap yazmak için de kullanılabilir.
- **Sunumlar:** Markdown ile Reveal.js gibi araçları kullanarak sunum oluşturabilirsiniz.
- **Eğitim Materyalleri:** Markdown eğitim materyalleri oluşturmak için uygundur.

## Markdown Temel Sözdizimi:

### Başlıklar:

```
markdown

# H1
## H2
### H3
#### H4
##### H5
###### H6

### Vurgu:

```markdown
*italic* or _italic_
**bold** or __bold__
**_italic and bold_** or *__italic and bold__*
~~strikethrough~~
```

### Listeler:

#### Sırasız:

```markdown
* Item 1
* Item 2
  * Subitem 2.1
  * Subitem 2.2
```

or 

```markdown
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2
```

#### Sıralı:

```markdown
1. First item
2. Second item
   1. Subitem 2.1
   2. Subitem 2.2
```

### Bağlantılar:

```markdown
[Google](https://www.google.com)
```

### Görseller:

```markdown
![Alt text](url_to_image)
```

### Blok alıntı:

```markdown
> This is a blockquote.
```

### Hiza Kodu:

```markdown
Here is `inline code`.
```

### Kod Bloğu:

Using three backticks:

<pre>
```
function example() {
  console.log("example");
}
```
</pre>

Or with syntax highlighting:

<pre>
```javascript
function example() {
  console.log("example");
}
```
</pre>

### Horizontal Rule:

```markdown
---
```

or 

```markdown
***
```

### Tables:

```markdown
| Header 1 | Header 2 |
| -------- | -------- |
| Cell1    | Cell2    |
| Cell3    | Cell4    |
```

### Task Lists:

```markdown
- [x] Task 1 (completed)
- [ ] Task 2 (not completed)
```

Unutmayın, farklı platformlar veya Markdown'un farklı sürümleri ek özelliklere veya küçük varyasyonlara sahip olabilir, ancak yukarıda belirtilenler temel ve yaygın olarak kullanılan sözdizimini kapsar.

Daha fazla okumak için [Markdown Guide](https://www.markdownguide.org/).


