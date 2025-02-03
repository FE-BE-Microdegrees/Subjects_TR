# Git

In this topic, we'll learn about the basics of Git and version control. We'll cover the importance of version control systems, the basics of Git, and the Git flow process.

- [Git](#git)
  - [Learning outcomes](#learning-outcomes)
  - [What is Git?](#what-is-git)
  - [Basic Git Architecture](#basic-git-architecture)
  - [Installing Git](#installing-git)
  - [Basic Git vocabulary](#basic-git-vocabulary)
  - [Basic Git Commands](#basic-git-commands)
  - [Graphical Git Clients](#graphical-git-clients)
    - [Some Popular Graphical Clients for Git:](#some-popular-graphical-clients-for-git)
    - [Reasons to Use Graphical Git Clients:](#reasons-to-use-graphical-git-clients)
  - [Git flow](#git-flow)
    - [1. **Main Branches**:](#1-main-branches)
    - [2. **Supporting Branches**:](#2-supporting-branches)
    - [**Basic Git Flow Process**:](#basic-git-flow-process)
  - [Git hosting platforms](#git-hosting-platforms)
  - [Excercises](#excercises)

## Learning outcomes

After completing this topic, you'll be able to:

- understand the importance of version control systems;
- describe the basics of Git and version control;
- describe the basic Git architecture;
- describe the basic Git vocabulary;
- describe the basic Git flow;

## What is Git?

```mermaid
    gitGraph
       commit id: "Create project"
       commit id: "Project base"
       branch nice_feature_branch
       checkout nice_feature_branch
       commit id: "Add frontend boilerplate"
       checkout nice_feature_branch
       commit id: "Connect frontend with API"
       checkout nice_feature_branch
       commit id: "Add frontend tests"
       checkout main
       merge nice_feature_branch id: "Basic frontend" tag: "Version 1.0"
       commit id: "Create documentation"
       checkout main
       commit id: "Update documentation"
```

**Git** is a distributed version control system (_DVCS_) used to track changes in source code during software development. It's designed to handle everything from small to very large projects with speed and efficiency. **Git** provides a way for multiple developers to collaborate on the same codebase without interfering with each other.

Git was created by Linus Torvalds in 2005 for the development of the Linux kernel. Its adoption has grown rapidly, and it's now the dominant version control system in the software industry. It's used by companies like Google, Facebook, Microsoft, and Twitter to manage their codebases.

Here are the key aspects and features of **Git**:

- **Distributed System**: Unlike centralized version control systems where there's a single central repository, in **Git**, every developer's copy of the code is also a repository that can contain the entire history and version tracking capabilities. This ensures redundancy and makes operations like branching and merging extremely efficient.
- **Branching and Merging**: **Git**'s branching model allows developers to create isolated branches for feature development or bug fixes. These branches can then be merged back into the main branch, typically known as the 'master' branch.
- **History**: **Git** tracks the entire history of the project. Every commit is checksummed and retrievable, ensuring integrity and traceability.
- **Staging Area**: **Git** introduces a unique concept of a _staging area_ or _index_. This is an intermediate area where commits can be formatted and reviewed before completing the commit.
- **Performance**: **Git** operations are performed locally, making it faster than many version control systems that rely on network operations.
- **Integrity**: **Git** uses a hashing algorithm called SHA-1 to checksum its data. This ensures the integrity of the version history.
- **Flexibility**: **Git** supports various workflows, from centralized to fully distributed, making it adaptable to different project needs.
- **Collaboration Platforms**: Platforms like _GitHub_, _GitLab_, and _Bitbucket_ enhance **Git**'s collaborative capabilities by providing code hosting, pull requests, code reviews, and issue tracking.
- **Free and Open Source**: **Git** is free software distributed under the terms of the GNU General Public License version 2.

## Basic Git Architecture

Git has a unique architecture and data model that makes it efficient and powerful. Here's a breakdown of the basic components of Git's architecture:

- **Blobs**:
  - Represents the content of a file in Git.
  - A blob holds the file data but doesn’t contain any metadata about the file.
  - It's a binary large object and is identified by a SHA-1 hash of its content.
- **Trees**:
  - Represents a directory or folder in Git.
  - A tree object maps names to blobs or trees (essentially, it can reference other trees for subdirectories).
  - Like blobs, trees are identified by a SHA-1 hash.
- **Commits**:
  - Represents a particular point in the repository's history.
  - A commit points to a tree that captures the state of the repository at a certain point in time.
  - Contains metadata such as:
    - Author
    - Committer
    - Date
    - Commit message
  - Each commit also points to its parent commit(s), forming a linked list. This is what creates the "history" in Git. Merge commits can point to multiple parents.
  - Identified by a SHA-1 hash.
- **Branches**:
  - A moving pointer to a commit.
  - When you create a branch, Git creates a pointer to the commit you're currently on.
  - As new commits are created, the branch pointer automatically moves to point to the latest commit.
  - The default branch in most repositories is named "master" (though a shift towards naming it "main" has been observed recently).
  - Branches allow for divergent development, where features or experiments can be developed in isolation before merging them back into the main codebase.

This architecture, built around a directed acyclic graph of objects, is what allows Git to efficiently track changes, create branches, and merge histories. The use of SHA-1 hashes ensures the integrity and consistency of the repository across clones and versions.

## Installing Git

Latest version of Git and instructions for installation can be found from [git-scm.com](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

## Basic Git vocabulary

Git has its own unique vocabulary, and understanding these terms is key to working effectively with Git. Here's a basic overview of some essential Git terminology:
- **Repository (Repo)**:
  - A directory or storage space where your project lives. It contains all of the project files and the entire revision history.
  - Can be local (on your computer) or remote (e.g., on a server or service like GitHub).
- **Commit**:
  - A set of changes or modifications to files. Each commit is uniquely identified by a SHA-1 hash code.
  - Represents a snapshot of the repository's files and directory structure at a particular point in time.
- **Branch**:
  - A parallel version of a repository. It diverges from the main working project into a separate area where you can work without affecting the main or "master" branch.
  - Useful for developing new features or testing out ideas.
- **Master or main**:
  - The default development branch. Whenever you create a Git repository, a branch named "master" or "main" is created, and becomes the active branch.
  - Note: There's a shift in the industry to rename this default branch to "main" for inclusivity reasons.
- **Clone**:
  - A copy of a repository that lives on your computer instead of on a server elsewhere or the original repository site.
  - `git clone [URL]` is the command used to clone (or copy) a repository from an existing URL.
- **Fork**:
  - A personal copy of another user's repository. Forking is used to suggest changes to someone else's project or to use someone else's project as a starting point for your own idea.
- **Pull**:
  - Refers to when you fetch in changes from a remote repository or branch and merge them into your current branch.
  - `git pull [remote] [branch_name]` is the command used to pull changes.
- **Push**:
  - Sending your committed changes to a remote repository.
  - `git push [remote] [branch_name]` is the command used to push your changes.
- **HEAD**:
  - A special pointer or reference to a specific commit in the repository. By default, it points to the latest commit in the branch you're currently on.
- **Merge**:
  - The process of integrating changes from one branch into another.
- **Merge Conflict**:
  - Occurs when competing changes are made to the same line of a file, or when one person edits a file and another person deletes the same file.
  - Git will highlight the differences and require you to choose which changes to keep.
- **Pull Request (PR)**:
  - On platforms like GitHub, a pull request is a way to propose changes from a fork or a branch which can then be merged into another branch, typically the master/main branch.
- **Remote**:
  - A version of your project that is hosted on the internet or network somewhere. You can have multiple remotes, and they are handy for collaborating with others.
- **Staging Area (or Index)**:
  - An intermediate area where commits can be formatted and reviewed before completing the commit.
  - `git add [file_name]` is used to add changes to the staging area.
- **Fetch**:
  - The act of downloading new data from a remote repository. Unlike `pull`, `fetch` gets the data but does not merge it.
- **Tag**:
  - A reference or pointer to a specific commit, often used to capture a point in history that is significant, such as a release version.

This overview covers the basic terms you'll encounter when starting with Git. As you delve deeper, you'll naturally come across more advanced concepts and terms.

## Basic Git Commands

Here's a basic overview of some essential Git commands and their descriptions:

- **`git init`**:
  - Initializes a new Git repository and starts tracking an existing directory.
  - Adds a hidden subfolder within the existing directory that houses the internal data structure required for version control.
- **`git clone [url]`**:
  - Creates a local copy of a project that already exists remotely.
  - The clone includes all the project’s files, history, and branches.
- **`git add [file-name.txt]`**:
  - Adds changes in the file to the staging area.
  - Prepares and packages up changes for a commit.
- **`git add .`**:
  - Adds all the changes in the current directory to the staging area (useful for tracking several changes across different files).
- **`git commit -m "[commit message]"`**:
  - Captures a snapshot of the project's currently staged changes.
- **`git status`**:
  - Shows the status of changes as untracked, modified, or staged.
- **`git branch`**:
  - Lists all local branches in the repository.
  - If you need to see all branches (including remote), use `git branch -a`.
- **`git branch [branch-name]`**:
  - Creates a new branch.
- **`git checkout [branch-name]`**:
  - Switches to the specified branch and updates the working directory.
  - Note: The command has evolved. You can now use `git switch [branch-name]` in newer versions of Git.
- **`git merge [branch-name]`**:
  - Merges the specified branch’s history into the current branch.
- **`git pull`**:
  - Updates your current local working branch with all new commits from the corresponding remote branch on GitHub.
- **`git push [remote-name] [branch-name]`**:
  - Pushes your local branch updates to the corresponding remote branch on GitHub.
- **`git log`**:
  - Displays an ordered list of all the commits which lead up to the current state of the branch.
  - There are many options to tailor the output format, like `git log --oneline` for a condensed view.
- **`git diff`**:
  - Shows the file differences that are not yet staged.
- **`git diff --staged`**:
  - Shows file differences when comparing the staged changes to the last commit.
- **`git remote add [alias] [url]`**:
  - Adds a remote repository to your local project.
- **`git remote -v`**:
  - Lists all remote repositories connected to the local project.
- **`git fetch`**:
  - Fetches all the updates from the remote repository (does not merge them).
- **`git revert [commit]`**:
  - Undoes all the changes made in a particular commit with a new commit.
- **`git reset`**:
  - Resets your staging area to match the most recent commit, but leaves the working directory unchanged. Useful for undoing `git add`.

This list covers the basics to get you started. Git is a deep tool with a variety of commands, and as you gain more experience, you'll discover many more advanced commands and options that can be used in various scenarios.

## Graphical Git Clients

**Graphical Git Clients** are applications that provide a visual interface to interact with Git, rather than relying solely on the command-line. They visually represent the version history, branches, and other aspects of a Git repository.

While graphical clients can be incredibly helpful, especially for those not comfortable with the command line, they do abstract away some of the intricacies of Git. For deeper, more complex operations, or to truly understand the inner workings of Git, familiarity with the command line is beneficial. Both approaches have their advantages, and many developers find a hybrid approach (using both command line and GUI) to be the most efficient.

### Some Popular Graphical Clients for Git:

- [**GitHub Desktop**](https://desktop.github.com/): This is the official GUI for GitHub. It’s open-source and cross-platform (available for macOS and Windows).
- [**Sourcetree**](https://www.sourcetreeapp.com/): Developed by Atlassian, it's a free tool available for macOS and Windows. It offers visual interaction with your repositories and supports Mercurial as well as Git.
- [**GitKraken**](https://www.gitkraken.com/): This cross-platform tool (available for Windows, macOS, and Linux) offers a vibrant and interactive interface. It's known for its graph visualization and has integrations with GitHub, GitLab, Bitbucket, and more.
- [**TortoiseGit**](https://tortoisegit.org/): Primarily for Windows, TortoiseGit integrates directly into the Windows shell, so you can right-click on a folder to access its features.

### Reasons to Use Graphical Git Clients:

- **User-Friendly**: For beginners, the command line can be intimidating. Graphical clients offer a more approachable and intuitive interface to interact with Git.
- **Visualization**: They provide a clear visual representation of branches, commits, merges, and more. This is especially helpful in understanding the flow and structure of commits in a repository.
- **Simplifies Complex Tasks**: Some Git tasks can be complex and verbose on the command line. GUI clients often simplify these processes into more manageable steps or provide a drag-and-drop interface.
- **Conflict Resolution**: Many graphical clients offer a visual way to resolve merge conflicts, making it clearer and sometimes easier than manually editing conflict markers in a text editor.
- **Integrated Tooling**: Graphical clients might come with built-in tools or integrations, such as Git blame, repository hosting services, and more.
- **Multitasking**: GUIs usually allow you to work on multiple repositories in separate tabs/windows, making context switching easier.
- **Immediate Feedback**: Many GUIs provide immediate visual feedback for most operations, such as the result of a merge or the changes introduced in a particular commit.
- **Support for Non-Git Operations**: Some GUIs offer features that aren't strictly Git operations, like the ability to open a file in a preferred editor, view the command history, or even run custom scripts.

## Git flow

Git Flow is a popular workflow methodology in Git that defines a structured approach to branching and merging. It provides a solid framework for managing larger projects and can simplify the process of collaborating with other developers on a shared repository. Below, I'll outline the Git Flow process, focusing on the role of branching:

### 1. **Main Branches**:

- **`main` (formerly `master`)**:
  - This branch contains the official release history.
  - All commits in the `main` branch represent a version of the software that is fully tested and deployable.
- **`develop`**:
  - Serves as an integration branch for features.
  - All the changes destined for the next release are integrated into this branch.

### 2. **Supporting Branches**:

These branches are used to aid parallel development, easily track features, prepare for releases, and quickly fix live issues.

- **Feature Branches**:
  - Branch off from: `develop`
  - Merge back into: `develop`
  - Naming convention: anything except `main`, `develop`, `release-*`, or `hotfix-*`
  - Purpose: Used to develop new features or enhancements. They exist as long as the feature is in development.

    ```mermaid
    graph LR
        A[develop] --> B[feature/feature_name]
        B --> A
    ```

- **Release Branches**:
  - Branch off from: `develop`
  - Merge back into: `main` and `develop`
  - Naming convention: `release-*`
  - Purpose: Used to prepare a new product version. This is where we tag our versions before they go into production. Bug fixes can be applied in this branch.

    ```mermaid
    graph LR
        A[develop] --> B[release/version_number]
        B --> C[main]
        B --> A
    ```

- **Hotfix Branches**:
  - Branch off from: `main`
  - Merge back into: `main` and `develop`
  - Naming convention: `hotfix-*`
  - Purpose: They arise from the necessity to act immediately upon an undesired state of the `main` branch. Used to quickly patch production releases.

    ```mermaid
    graph LR
        A[main] --> B[hotfix/issue]
        B --> A
        B --> C[develop]
    ```

### **Basic Git Flow Process**:

```mermaid
gitGraph
    commit id: "Create project"
    branch develop
    checkout develop
    commit id: "Project base"
    branch feature/nice_feature
    checkout feature/nice_feature
    commit id: "Add frontend boilerplate"
    commit id: "Connect frontend with API"
    commit id: "Add frontend tests"
    checkout develop
    merge feature/nice_feature
    branch release/1.0
    checkout release/1.0
    commit id: "Prepare for release"
    checkout main
    merge release/1.0 id: "Release Version 1.0" tag: "Version 1.0"
    checkout develop
    merge release/1.0
    checkout main
```

1. **Initialization**:
   Initialize a Git repository and then set up an empty `main` and `develop` branch.
2. **Start a New Feature**:
   For every new feature, create a new branch from `develop`, and name it according to the feature you're working on.
3. **Incorporate a Finished Feature**:
   Once the feature is complete and tested, it is merged back into `develop`. It awaits the next release cycle for integration into `main`.
4. **Release Time**:
   When enough features are ready, or a predetermined release point is reached, `develop` is branched off to a release branch, where final testing happens.
5. **Merge with Main**:
   Once the release branch is thoroughly tested, it is merged into `main` and tagged with a version number. It then also needs to be merged back into `develop` to ensure features added in the next cycle have the hotfixes and updates.
6. **Hotfixes**:
   If an issue is detected in the `main` branch and needs an immediate fix, a hotfix branch is created. Once the hotfix is complete, it's merged both into `main` (and tagged) and into `develop`.

Git Flow offers a rigorous framework for large-scale projects, but it might be overkill for smaller projects or teams. Some teams opt for simpler workflows, like GitHub flow or GitLab flow. Still, understanding Git Flow provides a solid foundation for how branching can be used in complex scenarios.

## Git hosting platforms

We could use Git locally, but it's more common to use a remote Git hosting platform. These platforms provide a centralized location for storing and collaborating on Git repositories. They also offer additional features like issue tracking, pull requests, code reviews, and more.

Here are some popular Git hosting platforms:

- [**GitHub**](https://github.com)
- [**GitLab**](https://gitlab.com)
- [**Bitbucket**](https://bitbucket.org)
- etc.

## Excercises

Try to explain the following concepts in your own words:
- What is Git and Version Control?
- Name at least four terms from the git vocabulary
- Name at least one Git hosting platform

Next steps:
- install `git` on your computer

# Git

Bu konuda, Git ve sürüm kontrolünün temellerini öğreneceğiz. Sürüm kontrol sistemlerinin önemi, Git’in temelleri ve Git akış süreci hakkında bilgi vereceğiz.

- [Git](#git)
  - [Öğrenme Çıktıları](#öğrenme-çıktıları)
  - [Git Nedir?](#git-nedir)
  - [Temel Git Mimarisi](#temel-git-mimarisi)
  - [Git Yükleme](#git-yükleme)
  - [Temel Git Kavramları](#temel-git-kavramları)
  - [Temel Git Komutları](#temel-git-komutları)
  - [Grafiksel Git İstemcileri](#grafiksel-git-istemcileri)
    - [Git İçin Popüler Grafiksel İstemciler:](#git-için-popüler-grafiksel-istemciler)
    - [Grafiksel Git İstemcileri Kullanmanın Nedenleri:](#grafiksel-git-istemcileri-kullanmanın-nedenleri)
  - [Git Akışı](#git-akışı)
    - [1. **Ana Dallar**:](#1-ana-dallar)
    - [2. **Destekleyici Dallar**:](#2-destekleyici-dallar)
    - [**Temel Git Akış Süreci**:](#temel-git-akış-süreci)
  - [Git Barındırma Platformları](#git-barındırma-platformları)
  - [Alıştırmalar](#alıştırmalar)

## Öğrenme Çıktıları

Bu konuyu tamamladıktan sonra şunları yapabileceksiniz:

- Sürüm kontrol sistemlerinin önemini anlayabileceksiniz;
- Git ve sürüm kontrolünün temellerini açıklayabileceksiniz;
- Temel Git mimarisini açıklayabileceksiniz;
- Temel Git kavramlarını açıklayabileceksiniz;
- Temel Git akışını açıklayabileceksiniz;

## Git Nedir?

```mermaid
    gitGraph
       commit id: "Projeyi oluştur"
       commit id: "Proje temeli"
       branch nice_feature_branch
       checkout nice_feature_branch
       commit id: "Frontend iskeletini ekle"
       checkout nice_feature_branch
       commit id: "Frontend'i API ile bağla"
       checkout nice_feature_branch
       commit id: "Frontend testlerini ekle"
       checkout main
       merge nice_feature_branch id: "Temel frontend" tag: "Versiyon 1.0"
       commit id: "Dokümantasyon oluştur"
       checkout main
       commit id: "Dokümantasyonu güncelle"

```

**Git**, yazılım geliştirme sırasında kaynak kodundaki değişiklikleri izlemek için kullanılan dağılmış bir versiyon kontrol sistemidir (_DVCS_). Küçükten çok büyük projelere kadar her şeyi hız ve verimlilikle yönetmek için tasarlanmıştır. **Git**, birden fazla geliştiricinin aynı kod tabanı üzerinde birbirlerine müdahale etmeden işbirliği yapmalarını sağlar.

Git, 2005 yılında Linux çekirdeğinin geliştirilmesi için Linus Torvalds tarafından yaratılmıştır. Benimsenmesi hızla artmış ve şimdi yazılım endüstrisindeki egemen versiyon kontrol sistemi haline gelmiştir. Google, Facebook, Microsoft ve Twitter gibi şirketler, kod tabanlarını yönetmek için Git'i kullanmaktadır.

İşte **Git**'in ana özellikleri ve özellikleri:

- **Dağıtık Sistem**: Tek bir merkezi depo bulunan merkezi versiyon kontrol sistemlerinin aksine, **Git**'te her geliştiricinin kod kopyası, tüm tarihçe ve versiyon takibi özelliklerini içerebilen bir depo olarak işlev görür. Bu, yedekliliği garanti eder ve dallanma (branching) ve birleştirme (merging) işlemlerini son derece verimli hale getirir.
- **Dallanma ve Birleştirme**: **Git**'in dallanma modeli, geliştiricilerin özellik geliştirme veya hata düzeltmeleri için izole dallar yaratmasına olanak tanır. Bu dallar daha sonra ana dal (genellikle 'master' dalı olarak bilinir) ile birleştirilebilir.
- **Geçmiş**: **Git** proje geçmişinin tamamını takip eder. Her commit, kontrol edilen ve geri alınabilen bir özet (checksum) içerir, bu da bütünlük ve izlenebilirlik sağlar.
- **Aşama Alanı (Staging Area)**: **Git**, _aşama alanı_ veya _index_ adı verilen benzersiz bir kavramı tanıtır. Bu, commit'lerin tamamlanmadan önce biçimlendirilebileceği ve gözden geçirilebileceği ara bir alandır.
- **Performans**: **Git** işlemleri yerel olarak gerçekleştirilir, bu da ağ işlemlerine dayanan birçok versiyon kontrol sistemine kıyasla daha hızlı olmasını sağlar.
- **Bütünlük**: **Git** verilerini kontrol etmek için SHA-1 adı verilen bir karma algoritması kullanır. Bu, versiyon geçmişinin bütünlüğünü garanti eder.
- **Esneklik**: **Git** çeşitli iş akışlarını destekler, merkezi sistemlerden tamamen dağıtık sistemlere kadar, bu da farklı proje ihtiyaçlarına uyum sağlamasını sağlar.
- **İşbirliği Platformları**: _GitHub_, _GitLab_ ve _Bitbucket_ gibi platformlar, **Git**'in işbirliği olanaklarını artırarak kod barındırma, pull request'ler, kod incelemeleri ve hata izleme gibi hizmetler sunar.
- **Ücretsiz ve Açık Kaynak**: **Git**, GNU Genel Kamu Lisansı sürüm 2 altında dağıtılan ücretsiz bir yazılımdır.

- ## Temel Git Mimarisi

Git, verimli ve güçlü olmasını sağlayan benzersiz bir mimariye ve veri modeline sahiptir. İşte Git'in temel bileşenlerinin bir açıklaması:

- **Bloklar (Blobs)**:
  - Git'teki bir dosyanın içeriğini temsil eder.
  - Bir blob, dosya verilerini tutar ancak dosya hakkında herhangi bir meta veriye sahip değildir.
  - Bu, ikili büyük bir nesnedir ve içeriğinin SHA-1 hash’i ile tanımlanır.
- **Ağaçlar (Trees)**:
  - Git'teki bir dizini veya klasörü temsil eder.
  - Bir ağaç nesnesi, isimleri blob'lara veya diğer ağaçlara (temelde alt dizinler için başka ağaçlara) eşler.
  - Blob'lar gibi, ağaçlar da bir SHA-1 hash’i ile tanımlanır.
- **Commit'ler (Commits)**:
  - Depodaki belirli bir zamanı temsil eder.
  - Bir commit, depo durumunu belirli bir zamanda yakalayan bir ağaca işaret eder.
  - Aşağıdaki gibi meta veriler içerir:
    - Yazar
    - Commit yapan kişi
    - Tarih
    - Commit mesajı
  - Her commit, aynı zamanda ebeveyn commit'ine işaret eder, böylece bağlı bir liste oluşturur. Bu, Git'teki "tarihçeyi" yaratır. Birleştirme commit'leri, birden fazla ebeveyn commit'ine işaret edebilir.
  - SHA-1 hash’i ile tanımlanır.
- **Dallar (Branches)**:
  - Bir commit’e hareket eden bir işaretçi.
  - Bir dal oluşturduğunuzda, Git, o anda bulunduğunuz commit'e bir işaretçi oluşturur.
  - Yeni commit'ler oluşturuldukça, dal işaretçisi otomatik olarak en son commit'e işaret edecek şekilde hareket eder.
  - Çoğu depoda varsayılan dal "master" olarak adlandırılır (ancak son zamanlarda "main" olarak adlandırılmaya doğru bir kayma gözlemlenmiştir).
  - Dallar, özellikler veya deneylerin ana kod tabanına birleştirilmeden önce izole bir şekilde geliştirilebilmesi için sapma geliştirmeye olanak tanır.

Bu mimari, yönlendirilmiş asiklik bir grafik üzerine kurulu olup, Git'in değişiklikleri verimli bir şekilde takip etmesini, dallar oluşturmasını ve tarihçeleri birleştirmesini sağlar. SHA-1 hash’lerinin kullanımı, depo bütünlüğünü ve tutarlılığını kopyalar ve sürümler arasında garanti eder.

## Git Kurulumu

Git'in en son sürümüne ve kurulum talimatlarına [git-scm.com](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) adresinden ulaşabilirsiniz.

## Temel Git Terminolojisi

Git, kendine özgü bir terminolojiye sahiptir ve bu terimleri anlamak, Git ile etkili çalışmanın anahtarıdır. İşte bazı temel Git terimlerinin genel bir özeti:

- **Depo (Repo)**:
  - Projenizin bulunduğu dizin veya depolama alanıdır. Tüm proje dosyalarını ve tüm revizyon geçmişini içerir.
  - Yerel (bilgisayarınızda) veya uzak (örneğin, bir sunucuda veya GitHub gibi bir hizmette) olabilir.
- **Commit**:
  - Dosyalarda yapılan değişiklik veya düzenlemeler setidir. Her commit, benzersiz bir SHA-1 hash kodu ile tanımlanır.
  - Depodaki dosyaların ve dizin yapısının belirli bir zaman dilimindeki anlık görüntüsünü temsil eder.
- **Dal (Branch)**:
  - Depo için paralel bir versiyonudur. Ana projeden ayrılarak, ana veya "master" dalını etkilemeden çalışabileceğiniz ayrı bir alana sapar.
  - Yeni özellikler geliştirmek veya fikirleri test etmek için kullanışlıdır.
- **Master veya main**:
  - Varsayılan geliştirme dalıdır. Bir Git deposu oluşturduğunuzda, "master" veya "main" adında bir dal oluşturulur ve bu dal aktif dal olur.
  - Not: Son zamanlarda, sektörde bu varsayılan dalın adını kapsayıcılık amaçlı olarak "main" olarak değiştirme eğilimi vardır.
- **Clone (Klonlama)**:
  - Depodan bilgisayarınıza kopyalanan bir reponun versiyonudur. Sunucuda veya başka bir yerdeki orijinal depo yerine bilgisayarınızda bulunur.
  - `git clone [URL]` komutu, mevcut bir URL'den bir depoyu klonlamak (veya kopyalamak) için kullanılır.
- **Fork (Çatal)**:
  - Başka bir kullanıcının deposunun kişisel kopyasıdır. Fork, başkasının projesine değişiklikler önerirken veya başkasının projesini kendi fikriniz için başlangıç noktası olarak kullanırken kullanılır.
- **Pull**:
  - Uzak bir depodan veya dalından değişiklikleri alıp, mevcut dalınıza birleştirmek anlamına gelir.
  - `git pull [remote] [branch_name]` komutu, değişiklikleri çekmek (pull) için kullanılır.
- **Push (Gönderme)**:
  - Yapılan commit'leri uzak bir depoya göndermek anlamına gelir.
  - `git push [remote] [branch_name]` komutu, değişikliklerinizi göndermek (push) için kullanılır.
- **HEAD**:
  - Depodaki belirli bir commit'e işaret eden özel bir işaretçi veya referanstır. Varsayılan olarak, şu anda bulunduğunuz dalda en son commit'e işaret eder.
- **Merge (Birleştirme)**:
  - Bir dalın değişikliklerini başka bir dala entegre etme sürecidir.
- **Merge Çatışması (Merge Conflict)**:
  - Aynı dosyanın aynı satırında çelişkili değişiklikler yapıldığında veya bir kişi bir dosyayı düzenlerken, başka bir kişi aynı dosyayı silerse çatışma meydana gelir.
  - Git, farkları vurgular ve hangi değişikliklerin saklanacağına karar vermeniz için sizi yönlendirir.
- **Pull Request (PR)**:
  - GitHub gibi platformlarda, bir pull request, bir forktan veya bir daldan değişiklikler önerme yoludur ve bu değişiklikler daha sonra başka bir dal ile birleştirilebilir, genellikle master/main dalına.
- **Remote (Uzak)**:
  - Projenizin internet veya ağ üzerinde barındırılan versiyonudur. Birden fazla uzak depo olabilir ve bunlar başkalarıyla işbirliği yaparken kullanışlıdır.
- **Aşama Alanı (veya Index)**:
  - Commit'lerin tamamlanmadan önce biçimlendirilebileceği ve gözden geçirilebileceği ara bir alandır.
  - `git add [file_name]` komutu, değişiklikleri aşama alanına eklemek için kullanılır.
- **Fetch (Alma)**:
  - Uzak bir depodan yeni veriler indirme işlemidir. `pull` komutunun aksine, `fetch` veriyi alır ancak birleştirme yapmaz.
- **Tag (Etiket)**:
  - Belirli bir commit'e referans veya işaretçidir, genellikle önemli bir tarihsel noktayı, örneğin bir sürümün yayınlandığı zamanı işaretlemek için kullanılır.

Bu genel bakış, Git'e yeni başlayanların karşılaşacağı temel terimleri kapsamaktadır. Daha derine indikçe, doğal olarak daha ileri düzey kavramlar ve terimler ile karşılaşacaksınız.

## Temel Git Komutları

İşte bazı temel Git komutlarının ve açıklamalarının genel bir özeti:

- **`git init`**:
  - Yeni bir Git deposu başlatır ve mevcut bir dizini izlemeye başlar.
  - Versiyon kontrolü için gerekli olan iç veri yapısını barındıran gizli bir alt klasör ekler.
- **`git clone [url]`**:
  - Zaten uzakta bulunan bir projenin yerel kopyasını oluşturur.
  - Klon, projenin tüm dosyalarını, geçmişini ve dallarını içerir.
- **`git add [file-name.txt]`**:
  - Dosyadaki değişiklikleri aşama alanına ekler.
  - Değişiklikleri commit için hazırlar ve paketler.
- **`git add .`**:
  - Geçerli dizindeki tüm değişiklikleri aşama alanına ekler (farklı dosyalarda yapılan birkaç değişikliği takip etmek için kullanışlıdır).
- **`git commit -m "[commit mesajı]"`**:
  - Projenin şu anki aşama alanındaki değişikliklerinin bir anlık görüntüsünü alır.
- **`git status`**:
  - Değişikliklerin durumunu izlenmeyen, değiştirilmiş veya aşamaya alınmış olarak gösterir.
- **`git branch`**:
  - Depodaki tüm yerel dalları listeler.
  - Tüm dalları (uzak dahil) görmek için `git branch -a` komutunu kullanın.
- **`git branch [branch-name]`**:
  - Yeni bir dal oluşturur.
- **`git checkout [branch-name]`**:
  - Belirtilen dala geçer ve çalışma dizinini günceller.
  - Not: Bu komut evrimleşti. Yeni Git sürümlerinde `git switch [branch-name]` komutunu kullanabilirsiniz.
- **`git merge [branch-name]`**:
  - Belirtilen dalın geçmişini, geçerli dalınıza birleştirir.
- **`git pull`**:
  - Geçerli yerel çalışma dalınızı, GitHub'daki ilgili uzak dal ile tüm yeni commit'lerle günceller.
- **`git push [remote-name] [branch-name]`**:
  - Yerel dal güncellemelerinizi GitHub'daki ilgili uzak dalına gönderir.
- **`git log`**:
  - Dalın mevcut durumuna kadar yapılan tüm commit'lerin sıralı listesini gösterir.
  - Çıktı formatını özelleştirmek için birçok seçenek vardır, örneğin `git log --oneline` komutu daha sıkıştırılmış bir görünüm sağlar.
- **`git diff`**:
  - Henüz aşamaya alınmamış dosya farklarını gösterir.
- **`git diff --staged`**:
  - Aşamaya alınmış değişikliklerin son commit ile karşılaştırılmasını gösterir.
- **`git remote add [alias] [url]`**:
  - Yerel projeye bir uzak depo ekler.
- **`git remote -v`**:
  - Yerel projeye bağlı tüm uzak depoları listeler.
- **`git fetch`**:
  - Uzak depodan tüm güncellemeleri alır (birleştirme yapmaz).
- **`git revert [commit]`**:
  - Belirli bir commit'te yapılan tüm değişiklikleri yeni bir commit ile geri alır.
- **`git reset`**:
  - Aşama alanını en son commit ile eşleşecek şekilde sıfırlar, ancak çalışma dizinini değiştirmez. `git add` komutunu geri almak için kullanışlıdır.

Bu liste, başlamanız için gerekli temel komutları kapsar. Git, çok çeşitli komutlara sahip derin bir araçtır ve deneyim kazandıkça farklı senaryolarda kullanılabilecek daha ileri düzey komutlar ve seçenekler keşfedeceksiniz.

## Grafiksel Git İstemcileri

**Grafiksel Git İstemcileri**, Git ile etkileşimde bulunmak için komut satırına dayanmak yerine görsel bir arayüz sağlayan uygulamalardır. Versiyon geçmişini, dalları ve bir Git deposunun diğer yönlerini görsel olarak temsil ederler.

Grafiksel istemciler son derece yardımcı olabilir, özellikle komut satırından rahatsız olmayanlar için, ancak Git'in bazı inceliklerini soyutlarlar. Daha derin ve karmaşık işlemler için veya Git'in iç işleyişini tam olarak anlamak için komut satırıyla aşina olmak faydalıdır. Her iki yaklaşımın da avantajları vardır ve birçok geliştirici, her iki yöntemi bir arada kullanmanın (komut satırı ve GUI) en

### Grafiksel Git İstemcilerini Kullanma Nedenleri:

- **Kullanıcı Dostu**: Başlangıç seviyesindeki kullanıcılar için komut satırı korkutucu olabilir. Grafiksel istemciler, Git ile etkileşim kurmak için daha erişilebilir ve sezgisel bir arayüz sunar.
- **Görselleştirme**: Dalları, commit'leri, birleştirmeleri ve daha fazlasını net bir şekilde görsel olarak temsil ederler. Bu, bir deponun commit akışını ve yapısını anlamada özellikle faydalıdır.
- **Karmaşık Görevleri Basitleştirir**: Bazı Git görevleri komut satırında karmaşık ve uzun olabilir. GUI istemcileri bu işlemleri daha yönetilebilir adımlara indirger veya sürükle-bırak arayüzü sağlar.
- **Çatışma Çözümü**: Birçok grafiksel istemci, birleştirme çatışmalarını çözmek için görsel bir yol sunar, bu da metin düzenleyicilerindeki çatışma işaretçilerini manuel olarak düzenlemekten bazen daha kolay ve daha anlaşılır olabilir.
- **Entegre Araçlar**: Grafiksel istemciler, Git blame, depo barındırma hizmetleri gibi yerleşik araçlar veya entegrasyonlarla birlikte gelebilir.
- **Çoklu Görev Desteği**: GUI'ler genellikle birden fazla depo üzerinde ayrı sekmeler/pencerelerle çalışmanıza olanak tanır, bu da bağlam değiştirmeyi daha kolay hale getirir.
- **Anında Geri Bildirim**: Birçok GUI, birleştirme sonucu veya belirli bir commit'te yapılan değişiklikler gibi çoğu işlem için anında görsel geri bildirim sağlar.
- **Git Dışı Operasyonları Destekler**: Bazı GUI'ler, bir dosyayı tercih edilen editörde açma, komut geçmişini görüntüleme veya özel betikler çalıştırma gibi Git işlemleri dışındaki özellikler sunar.

## Git Akışı

Git Akışı, Git’te popüler bir iş akışı metodolojisidir ve dallanma ve birleştirme için yapılandırılmış bir yaklaşım tanımlar. Büyük projeleri yönetmek için sağlam bir çerçeve sağlar ve başka geliştiricilerle ortak bir depoda iş birliği yapmayı basitleştirebilir. Aşağıda, Git Akışı sürecini, özellikle dal kullanımı açısından özetleyeceğim:

### 1. **Ana Dallar**:

- **`main` (eski adıyla `master`)**:
  - Bu dal, resmi sürüm geçmişini içerir.
  - `main` dalındaki tüm commit'ler, tamamen test edilmiş ve dağıtıma hazır bir yazılım sürümünü temsil eder.
- **`develop`**:
  - Özellikler için birleştirme dalı olarak hizmet eder.
  - Bir sonraki sürüm için yapılacak tüm değişiklikler bu dala entegrasyon edilir.

### 2. **Destekleyici Dallar**:

Bu dallar, paralel geliştirmeyi desteklemek, özellikleri kolayca takip etmek, sürüme hazırlık yapmak ve canlı sorunları hızlıca çözmek için kullanılır.

- **Özellik Dalları**:
  - Şuradan dalar: `develop`
  - Geri birleştirilir: `develop`
  - İsimlendirme kuralı: `main`, `develop`, `release-*` veya `hotfix-*` dışında herhangi bir şey.
  - Amaç: Yeni özellikler veya iyileştirmeler geliştirmek için kullanılır. Özellik geliştirilene kadar var olurlar.

    ```mermaid
    graph LR
        A[develop] --> B[feature/feature_name]
        B --> A
    ```

- **Sürüm Dalları**:
  - Şuradan dalar: `develop`
  - Geri birleştirilir: `main` ve `develop`
  - İsimlendirme kuralı: `release-*`
  - Amaç: Yeni bir ürün sürümü hazırlamak için kullanılır. Bu dalda sürümler etiketlenir ve üretime gitmeden önce hata düzeltmeleri yapılabilir.

    ```mermaid
    graph LR
        A[develop] --> B[release/version_number]
        B --> C[main]
        B --> A
    ```

- **Hotfix Dalları**:
  - Şuradan dalar: `main`
  - Geri birleştirilir: `main` ve `develop`
  - İsimlendirme kuralı: `hotfix-*`
  - Amaç: `main` dalındaki istenmeyen bir duruma hemen müdahale edilmesi gerektiğinde ortaya çıkar. Üretim sürümlerini hızla yama yapmak için kullanılır.

    ```mermaid
    graph LR
        A[main] --> B[hotfix/issue]
        B --> A
        B --> C[develop]
    ```

### **Temel Git Akışı Süreci**:

```mermaid
gitGraph
    commit id: "Proje oluşturuldu"
    branch develop
    checkout develop
    commit id: "Proje tabanı"
    branch feature/nice_feature
    checkout feature/nice_feature
    commit id: "Frontend iskeleti eklendi"
    commit id: "Frontend API ile bağlantı kuruldu"
    commit id: "Frontend testleri eklendi"
    checkout develop
    merge feature/nice_feature
    branch release/1.0
    checkout release/1.0
    commit id: "Sürüme hazırlanıyor"
    checkout main
    merge release/1.0 id: "Sürüm 1.0 Yayınlandı" tag: "Sürüm 1.0"
    checkout develop
    merge release/1.0
    checkout main

```

1. **Başlatma**:
   Bir Git deposu başlatın ve ardından boş bir `main` ve `develop` dalı oluşturun.
2. **Yeni Bir Özellik Başlatma**:
   Her yeni özellik için, `develop` dalından yeni bir dal oluşturun ve üzerinde çalıştığınız özelliğe göre adlandırın.
3. **Tamamlanan Özelliği Dahil Etme**:
   Özellik tamamlandığında ve test edildiğinde, geri `develop` dalına birleştirilir. Bir sonraki sürüm döngüsü için `main` dalına entegrasyon bekler.
4. **Sürüm Zamanı**:
   Yeterince özellik hazır olduğunda veya önceden belirlenmiş bir sürüm noktası ulaşıldığında, `develop` dalı bir sürüm dalına ayrılır ve burada son testler yapılır.
5. **Main ile Birleştirme**:
   Sürüm dalı yeterince test edildikten sonra, `main` dalına birleştirilir ve bir sürüm numarası ile etiketlenir. Daha sonra, gelecek döngüdeki özelliklerin hotfix'ler ve güncellemelerle uyumlu olmasını sağlamak için tekrar `develop` dalına birleştirilmesi gerekir.
6. **Hotfix'ler**:
   Eğer `main` dalında bir sorun tespit edilirse ve hemen bir düzeltme yapılması gerekirse, bir hotfix dalı oluşturulur. Hotfix tamamlandığında, hem `main` dalına (etiketlenmiş olarak) hem de `develop` dalına birleştirilir.

Git Flow, büyük ölçekli projeler için katı bir çerçeve sunar, ancak küçük projeler veya ekipler için fazla karmaşık olabilir. Bazı ekipler, GitHub Flow veya GitLab Flow gibi daha basit iş akışlarını tercih edebilir. Yine de Git Flow'u anlamak, karmaşık senaryolarda dallanmanın nasıl kullanılacağı konusunda sağlam bir temel sağlar.

## Git Hosting Platformları

Git'i yerel olarak kullanabiliriz, ancak daha yaygın olarak bir uzaktan Git hosting platformu kullanılır. Bu platformlar, Git depolarını saklamak ve üzerinde iş birliği yapmak için merkezi bir yer sağlar. Ayrıca, hata izleme, pull request'ler, kod incelemeleri ve daha fazlası gibi ek özellikler sunar.

İşte bazı popüler Git hosting platformları:

- [**GitHub**](https://github.com)
- [**GitLab**](https://gitlab.com)
- [**Bitbucket**](https://bitbucket.org)
- vb.

## Alıştırmalar

Aşağıdaki kavramları kendi kelimelerinizle açıklamayı deneyin:
- Git ve Sürüm Kontrolü nedir?
- Git terimlerinden en az dört tanesini sayın.
- En az bir Git hosting platformu ismi sayın.

Sonraki adımlar:
- Bilgisayarınıza `git` yükleyin
