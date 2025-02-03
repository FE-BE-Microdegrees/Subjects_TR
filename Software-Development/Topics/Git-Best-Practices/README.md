# Git and GitHub Best Practices

In this topic, we will learn about the best practices for using Git and GitHub. We will explore the best practices for Git and GitHub and learn how to apply them in a software development project.

![Git Best Practices](Git-Best-Practices.webp)

- [Git and GitHub Best Practices](#git-and-github-best-practices)
  - [Learning Outcomes](#learning-outcomes)
  - [Git Best Practices](#git-best-practices)
  - [GitHub Best Practices](#github-best-practices)

## Learning Outcomes

After completing this topic, you will be able to:

- Describe the best practices for using Git and GitHub;
- Apply Git and GitHub best practices in a software development project.

Using Git and GitHub effectively involves more than just knowing the commands and tools. Following best practices ensures that the development process is smooth, the project history remains clean, and team collaboration is efficient.

Here is an overview of the best practices for both Git and GitHub:

## Git Best Practices

1. **Commit Often, Push Less Frequently:**
   - Make frequent, smaller commits that cover a single logical change (e.g., fixing a bug or adding a feature). This makes it easier to understand the history and isolate issues.
2. **Write Meaningful Commit Messages:**
   - Start with a short, descriptive title. If more detail is needed, add a thorough description in the body. This helps other developers understand why the change was made and how it affects the codebase.
3. **Use Branches:**
   - Never work directly on the `main` or `master` branch. Use feature branches for each new feature or bug fix.
   - Delete branches after merging them to keep the repository clean.
4. **Avoid Changing Published History:**
   - Once commits are pushed to a branch, avoid using commands that rewrite history (e.g., `rebase` or `force push`), unless you are absolutely sure of what you are doing.
5. **Synchronize Regularly:**
   - Pull frequently from the main repository to integrate changes and resolve conflicts early.
6. **Resolve Conflicts Immediately:**
   - Address and resolve merge conflicts as soon as they arise.
7. **Use a `.gitignore` File:**
   - Add files that should not be in the repository (e.g., secrets, caches, log files) to the `.gitignore` file.
8. **Backup:**
   - Although Git is a version control system, it is a good practice to have backups of your repository, especially if Git is hosted locally.

## GitHub Best Practices

1. **Use Descriptive Repository Names:**
   - Names should hint at the project's purpose or content.
2. **Add a `README.md`:**
   - Always include a `README.md` file in your repositories. It should explain the project, how to set it up, how to install dependencies, how to contribute, and other relevant information. Note that the `README.md` name is written in uppercase letters.
3. **Use Issue and Pull Request Templates:**
   - Templates guide contributors to provide necessary information when creating issues or pull requests.
4. **Protect Your Main Branch:**
   - Use branch protection rules to ensure that the `main` or `master` branch cannot be pushed to directly and require pull request reviews before merging.
5. **Use Labels:**
   - Organize issues and pull requests with labels (e.g., `bug`, `enhancement`).
6. **Code Reviews:**
   - Always review pull requests before merging. This ensures better code quality and consistency as the code is reviewed by more than one person.
7. **Communicate with the Community:**
   - Respond to issues and pull requests in a timely manner. Thank and encourage contributors, even if their contributions are not added to the project.
8. **Use GitHub Actions:**
   - Automate testing, building, and deployment processes with GitHub Actions.
9. **Keep Personal Data Out of the Repository:**
   - Never store sensitive information like **passwords**, **API keys**, or **secrets** in your repositories. Use GitHub's secrets feature or external tools like environment variables for this purpose.
10. **Regularly Review Permissions and Access:**
    - Ensure that only necessary contributors have access to your repository.

Following these best practices ensures that your use of Git and GitHub is effective, your project history remains meaningful and organized, and collaboration is smooth and productive.

# Git ve GitHub En İyi Uygulamaları

Bu konuda, Git ve GitHub'ı kullanmanın en iyi uygulamalarını öğreneceğiz. Git ve GitHub için en iyi uygulamaları keşfedecek ve bir yazılım geliştirme projesinde nasıl uygulayacağımızı öğreneceğiz.

![Git En İyi Uygulamalar](Git-Best-Practices.webp)

- [Git ve GitHub En İyi Uygulamaları](#git-ve-github-en-iyi-uygulamalari)
  - [Öğrenme Çıktıları](#ogrenme-ciktilari)
  - [Git En İyi Uygulamaları](#git-en-iyi-uygulamalari)
  - [GitHub En İyi Uygulamaları](#github-en-iyi-uygulamalari)

## Öğrenme Çıktıları

Bu konuyu tamamladıktan sonra:

- Git ve GitHub kullanımı için en iyi uygulamaları açıklayabileceksiniz;
- Bir yazılım geliştirme projesinde Git ve GitHub en iyi uygulamalarını uygulayabileceksiniz.

Git ve GitHub'ı etkili bir şekilde kullanmak, yalnızca komutları ve araçları bilmekten fazlasını gerektirir. En iyi uygulamaları takip etmek, geliştirme sürecinin sorunsuz olmasını, proje geçmişinin temiz kalmasını ve ekip iş birliğinin verimli olmasını sağlar.

İşte Git ve GitHub için en iyi uygulamaların bir özeti:

## Git En İyi Uygulamaları

1. **Sık Sık Commit Yapın, Daha Az Push Yapın:**
   - Bir hatayı düzeltmek veya bir özellik eklemek gibi tek bir mantıksal değişikliği kapsayan küçük, sık commit'ler yapın. Bu, geçmişi anlamayı ve sorunları izole etmeyi kolaylaştırır.
2. **Anlamlı Commit Mesajları Yazın:**
   - Kısa, açıklayıcı bir başlıkla başlayın. Daha fazla ayrıntıya ihtiyaç varsa, gövde kısmında detaylı bir açıklama ekleyin. Bu, diğer geliştiricilerin yapılan değişikliğin nedenini ve kod tabanını nasıl etkilediğini anlamasına yardımcı olur.
3. **Branch Kullanın:**
   - Hiçbir zaman doğrudan `main` veya `master` branch'inde çalışmayın. Her yeni özellik veya hata düzeltmesi için özellik branch'leri kullanın.
   - Depoyu temiz tutmak için branch'leri birleştirdikten sonra silin.
4. **Yayınlanmış Geçmişi Değiştirmekten Kaçının:**
   - Commit'ler bir branch'e push edildikten sonra, geçmişi yeniden yazan komutları (`rebase` veya `force push` gibi) kullanmaktan kaçının, emin olmadıkça kullanmayın.
5. **Düzenli Olarak Senkronize Edin:**
   - Ana depodan sık sık pull yaparak değişiklikleri entegre edin ve çatışmaları erken çözün.
6. **Çatışmaları Hemen Çözün:**
   - Merge çatışmalarını ortaya çıkar çıkmaz ele alın ve çözün.
7. **Bir `.gitignore` Dosyası Kullanın:**
   - Depoda olmaması gereken dosyaları (örneğin, sırlar, önbellekler, günlük dosyaları) `.gitignore` dosyasına ekleyin.
8. **Yedekleme Yapın:**
   - Git bir sürüm kontrol sistemi olmasına rağmen, özellikle Git yerel olarak barındırılıyorsa, deponuzun yedeklerini almak iyi bir uygulamadır.

## GitHub En İyi Uygulamaları

1. **Açıklayıcı Depo İsimleri Kullanın:**
   - İsimler, projenin amacı veya içeriği hakkında ipucu vermelidir.
2. **Bir `README.md` Ekleyin:**
   - Her zaman depolarınıza bir `README.md` dosyası ekleyin. Bu dosya, projeyi, nasıl kurulacağını, bağımlılıkların nasıl yükleneceğini, nasıl katkıda bulunulacağını ve diğer ilgili bilgileri açıklamalıdır. `README.md` dosya adı büyük harflerle yazılır.
3. **Issue ve Pull Request Şablonları Kullanın:**
   - Şablonlar, katkıda bulunanların issue veya pull request oluştururken gerekli bilgileri sağlamasına rehberlik eder.
4. **Ana Branch'i Koruyun:**
   - Branch koruma kuralları kullanarak `main` veya `master` branch'ine doğrudan push yapılmasını engelleyin ve birleştirme işlemlerinden önce pull request incelemeleri gerektirin.
5. **Etiketler Kullanın:**
   - Issue ve pull request'leri `bug`, `enhancement` gibi etiketlerle organize edin.
6. **Kod İncelemeleri:**
   - Birleştirmeden önce pull request'leri her zaman gözden geçirin. Bu, kod kalitesinin ve tutarlılığın daha iyi olmasını sağlar, çünkü kod birden fazla kişi tarafından incelenir.
7. **Toplulukla İletişim Kurun:**
   - Issue ve pull request'lere zamanında yanıt verin. Katkıda bulunanlara teşekkür edin ve onları teşvik edin, hatta katkıları projeye eklenmese bile.
8. **GitHub Actions Kullanın:**
   - GitHub Actions ile test, derleme ve dağıtım süreçlerini otomatikleştirin.
9. **Kişisel Verileri Depodan Uzak Tutun:**
   - **Şifreler**, **API anahtarları** veya **gizli bilgiler** gibi hassas bilgileri asla depolarınıza koymayın. Bunun yerine GitHub'ın secrets özelliğini veya ortam değişkenleri gibi harici araçları kullanın.
10. **İzinleri ve Erişimi Düzenli Olarak Gözden Geçirin:**
    - Sadece gerekli katkıda bulunanların deponuza erişimi olduğundan emin olun.

Bu en iyi uygulamaları takip etmek, Git ve GitHub kullanımınızı etkili hale getirir, proje geçmişinizi anlamlı ve düzenli tutar, ve iş birliğini sorunsuz ve verimli hale getirir.
