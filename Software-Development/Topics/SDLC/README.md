# Software Development Life Cycle (SDLC):

- [Software Development Life Cycle (SDLC):](#software-development-life-cycle-sdlc)
  - [Learning Outcomes:](#learning-outcomes)
  - [Typical SDLC Phases:](#typical-sdlc-phases)
    - [Planning and Requirements Definition](#planning-and-requirements-definition)
    - [Requirements Definition](#requirements-definition)
    - [Design](#design)
    - [Development](#development)
    - [Testing](#testing)
    - [Deployment](#deployment)
    - [Maintenance and Support](#maintenance-and-support)
    - [Review and Feedback](#review-and-feedback)
  - [Importance of SDLC:](#importance-of-sdlc)
  - [Common SDLC Models:](#common-sdlc-models)
    - [**Waterfall Model:**](#waterfall-model)
    - [**Lean**](#lean)
    - [**Spiral Model:**](#spiral-model)
    - [**Agile Model:**](#agile-model)
    - [**Feature-Driven Development (FDD)**](#feature-driven-development-fdd)
    - [**Extreme Programming (XP)**](#extreme-programming-xp)
    - [**Kanban:**](#kanban)
    - [**Scrum:**](#scrum)
  - [Excercises and Assignments](#excercises-and-assignments)

## Learning Outcomes:

After completing this topic, you'll be able to:

- understand the Software Development Life Cycle (SDLC);
- identify the different phases of the SDLC;
- describe the importance of SDLC;
- identify the common SDLC models.
- apply SDLC principles to software development.

The Software Development Life Cycle (SDLC) is a systematic process for planning, creating, testing, deploying, and maintaining software. It defines the stages and tasks involved in producing software from inception to retirement.

```mermaid
graph TD
  A(Planning) --> B(Requirement Analysis)
  B --> C(System Design)
  C --> D(Implementation/Development)
  D --> E(Testing)
  E --> F(Deployment)
  F --> G(Maintenance and Support)
  G --> H(Review and Feedback)
  H --> A

```

## Typical SDLC Phases

The Software Development Life Cycle (SDLC) is a structured process that defines the stages or steps involved in producing software. While there are various models or frameworks for SDLC, many share common phases. Here is an overview of typical steps involved:

### Planning and Requirements Definition

Requirement analysis is the most crucial and fundamental stage of SDLC. It is conducted by team members in collaboration with clients, sales departments, market research, and industry experts. This information is then used to plan the basic approach to the project and conduct a feasibility study in economic, labor, and technical areas.

The planning stage also involves planning for quality assurance requirements and identifying project-related risks. The result of the technical feasibility study is to define different technical approaches that can be followed to successfully implement the project with minimal risks.

This stage may include the following steps:
- Determining project scope.
- Identifying potential risks, constraints, and resources.
- Creating a project plan (including schedules, milestones, and budget estimates).
- Conducting user research to understand user needs and expectations.

### Requirements Definition

Once the requirements analysis is done, the next step is to clearly define and document product requirements and get approval from the client or market analysts. This is done through the Software Requirement Specification (SRS), which contains all the product requirements planned and developed throughout the project life cycle.

This stage may include the following activities:
- Gathering and documenting requirements and needs.
- Collecting specifications from stakeholders (end-users, clients, etc.).
- Feasibility analysis of requirements.
- Prioritizing and confirming the list of requirements.

### Design

The Software Requirements Specification serves as the basis for product architects to come up with the best architecture for the product to be developed. Based on the requirements defined in the Software Requirements Specification, more than one product architecture design solution is usually proposed and documented in the Design Document Specification (DDS).

The Design Document Specification is reviewed by all key stakeholders, and the best design solution for the product is selected based on various parameters such as risk assessment, product robustness, design modularity, budget, and time constraints.

The design approach clearly defines all product architecture modules along with their communication and data flow presentation with external and third-party modules (if any). The interior design of all modules of the proposed architecture should be clearly defined down to the minutest details in the Design Document Specification.

In this stage, the user interface (UI) and user experience (UX) design are also created, which are crucial for engaging users and simplifying the use of the product.
- Translating requirements into system specifications.
- Designing system architecture and framework.
- UX (User Experience) and UI (User Interface) design.
- Selection of appropriate technologies, platforms, and tools.

### Development

In this SDLC phase, actual development and building of the product begin. Programming code is generated at this stage according to the design document specification. If the design has been detailed and organized properly, code can be generated without much trouble.

Developers must follow the coding guidelines defined by their organization, and programming tools such as compilers, debuggers, etc., are used to generate the code. Different high-level programming languages like C, C++, Pascal, Java, Javascript, and PHP are used for coding, depending on the type of software being developed.
- Writing code.
- Transforming design into functional software.
- Integrating various components and ensuring their cooperation.

### Testing

This stage is usually a subset of all stages, as in modern SDLC models, testing activities mostly cover all SDLC stages. However, this stage refers to the product testing stage, where defects in the product are reported, tracked, corrected, and retested until the product reaches the quality standards defined in the SRS.
- Verifying compliance with software requirements.
- Correcting and verifying bugs and discrepancies.
- Applying various testing methods (unit testing, integration testing, manual testing, etc.).
- Validating software functionality, performance, security, and usability.

### Deployment

Once the product is tested and ready for deployment, it is officially released to the relevant market. Sometimes, the product deployment is carried out in stages according to the organization's business strategy. The product might initially be released in a limited segment and tested in a real business environment (UAT – User Acceptance Testing).

The product might then be released in its form or along with recommended enhancements in the target market segment based on feedback.
- Preparing the software launch environment.
- Installing and implementing software in the production environment.
- Training end-users if necessary.
- Monitoring software performance and ensuring smooth operation.

### Maintenance and Support

After the software deployment, it is crucial to ensure that it operates without issues and meets user needs. This involves software maintenance and support to ensure that the software remains operational, efficient, and relevant over time.
- Resolving issues and bugs that arise post-deployment.
- Creating updates, fixes, or enhancements based on user feedback.
- Ensuring that the software remains operational, efficient, and relevant over time.
- Addressing security vulnerabilities and compatibility issues.

### Review and Feedback

The final stage involves reviewing the entire SDLC process and collecting feedback to identify what can be improved in the next iteration or software version. This stage is essential to ensure that the software development process is continuously improved and meets user needs.
- Collecting feedback from stakeholders and end-users.
- Analyzing software performance and identifying areas for improvement.
- Planning the next iteration or software version.

Each of these phases can be iterative, especially in agile or spiral models, where software is developed in cycles or iterations. The exact steps and their order may vary depending on the chosen SDLC model, organizational processes, and the nature of the project. However, the goal is the same: to produce quality software that meets user needs and expectations in the most efficient way possible.

## Importance of SDLC

- **Structured Process:** SDLC provides a structured approach to software development, ensuring that critical steps are not missed.
- **Quality Assurance:** Each phase of SDLC has specific outcomes and review processes that lead to better software quality.
- **Risk Management:** Early identification of possible issues or risks allows for timely mitigation.
- **Project Management:** SDLC provides a clear framework for monitoring project progress, allocating resources, and adhering to budgets.
- **Stakeholder Communication:** By defining clear phases and outcomes, stakeholders are kept informed about progress and expected results.
- **Efficiency and Cost-Effectiveness:** By systematically addressing the software development process, wastage is minimized and efficiency is maximized.
- **Documentation:** Proper documentation is an integral part of SDLC, ensuring that knowledge is preserved and system details are well understood.

## Common SDLC Models:

### **Waterfall Model:**

- **Description:** A linear and sequential approach where each phase must be completed before the next one starts. It's the earliest SDLC approach.
- **Pros:** Clear structure, simple to understand, well-defined stages.
- **Cons:** Difficult to make changes after the phase is complete, not suitable for complex projects.

### **Lean**

- **Description:** Originating from manufacturing, it focuses on resource optimization and customer value delivery. It aims to cut out any "waste" from the process.
- **Pros:** Efficient resource utilization, focuses on delivering value.
- **Cons:** May overlook necessary tasks as "waste," requires a deep understanding to implement correctly.

### **Spiral Model:**

- **Description:** Combines the design phase of the Waterfall model with the iterative philosophy of prototyping. Focuses on risk assessment at every spiral.
- **Pros:** Focus on risk management, flexibility in design and requirements.
- **Cons:** Can be expensive, requires risk assessment expertise.

### **Agile Model:**

- **Description:** An iterative approach to software delivery that builds software incrementally, with a focus on customer feedback and rapid iterations.
- **Pros:** Flexible, promotes iterative feedback, encourages customer involvement.
- **Cons:** Less predictability, can be hard to grasp for those used to traditional methods.

### **Feature-Driven Development (FDD)**

- **Description:** An iterative and incremental software development process driven by feature lists.
- **Pros:** Focus on building and delivering tangible, client-valued functions.
- **Cons:** Not as flexible as other Agile methodologies, requires detailed documentation.

### **Extreme Programming (XP)**

- **Description:** An Agile framework that emphasizes customer satisfaction, with frequent "releases" in short development cycles aimed at improving productivity and introducing checkpoints.
- **Pros:** Emphasizes code quality, encourages customer involvement.
- **Cons:** Requires extensive customer involvement, can be intense for developers.

### **Kanban:**

- **Description:** A visual approach to process management, taking cues from lean manufacturing and emphasizing just-in-time delivery.
- **Pros:** Flexibility, continuous delivery, visual nature helps in identifying bottlenecks.
- **Cons:** Less structured, can lead to scope creep if not managed correctly.

### **Scrum:**

- **Description:** A type of Agile methodology that organizes work into cycles known as "Sprints," typically lasting 2-4 weeks.
- **Pros:** Regular product deliveries, high visibility, adaptability.
- **Cons:** Requires experienced team members, scope can sometimes be too flexible.

In conclusion, the choice of SDLC framework often depends on the nature of the project, organizational preferences, team size, project scope, and other factors. The ultimate aim is to produce high-quality software that meets user expectations while maintaining a time and budgetary framework.

## Excercises and Assignments

# Yazılım Geliştirme Yaşam Döngüsü (SDLC):

- [Yazılım Geliştirme Yaşam Döngüsü (SDLC):](#yazılım-geliştirme-yaşam-döngüsü-sdlc)
  - [Öğrenme Sonuçları:](#öğrenme-sonuçları)
  - [Tipik SDLC Aşamaları:](#tipik-sdlc-aşamaları)
    - [Planlama ve Gereksinim Tanımlaması](#planlama-ve-gereksinim-tanımlaması)
    - [Gereksinim Tanımlaması](#gereksinim-tanımlaması)
    - [Tasarım](#tasarım)
    - [Geliştirme](#geliştirme)
    - [Test Etme](#test-etme)
    - [Dağıtım](#dağıtım)
    - [Bakım ve Destek](#bakım-ve-destek)
    - [İnceleme ve Geribildirim](#inceleme-ve-geribildirim)
  - [SDLC'nin Önemi:](#sdlc'nin-önemi)
  - [Yaygın SDLC Modelleri:](#yaygın-sdlc-modelleri)
    - [**Waterfall Modeli:**](#waterfall-modeli)
    - [**Lean**](#lean)
    - [**Spiral Modeli:**](#spiral-modeli)
    - [**Agile Modeli:**](#agile-modeli)
    - [**Özellik Odaklı Geliştirme (FDD)**](#özellik-odaklı-geliştirme-fdd)
    - [**Extreme Programming (XP)**](#extreme-programming-xp)
    - [**Kanban:**](#kanban)
    - [**Scrum:**](#scrum)
  - [Alıştırmalar ve Görevler](#alıştırmalar-ve-görevler)

## Öğrenme Sonuçları:

Bu konuyu tamamladıktan sonra şunları yapabileceksiniz:

- Yazılım Geliştirme Yaşam Döngüsü'nü (SDLC) anlayabileceksiniz;
- SDLC'nin farklı aşamalarını tanımlayabileceksiniz;
- SDLC'nin önemini açıklayabileceksiniz;
- Yaygın SDLC modellerini tanımlayabileceksiniz;
- SDLC ilkelerini yazılım geliştirmeye uygulayabileceksiniz.

Yazılım Geliştirme Yaşam Döngüsü (SDLC), yazılım planlama, oluşturma, test etme, dağıtım ve bakım sürecini sistematik bir şekilde tanımlar. Yazılımın başlangıcından emekliliğine kadar olan aşamaları ve görevleri tanımlar.

```mermaid
graph TD
  A(Planlama) --> B(Gereksinim Analizi)
  B --> C(Sistem Tasarımı)
  C --> D(Uygulama/Geliştirme)
  D --> E(Test Etme)
  E --> F(Dağıtım)
  F --> G(Bakım ve Destek)
  G --> H(İnceleme ve Geribildirim)
  H --> A

```
## Tipik SDLC Aşamaları

Yazılım Geliştirme Yaşam Döngüsü (SDLC), yazılım üretiminde yer alan aşamaları veya adımları tanımlayan yapılandırılmış bir süreçtir. Çeşitli SDLC modelleri veya çerçeveleri olsa da, çoğu ortak aşamalara sahiptir. İşte tipik adımların genel bir özeti:

### Planlama ve Gereksinim Tanımlaması

Gereksinim analizi, SDLC'nin en kritik ve temel aşamasıdır. Bu aşama, ekip üyeleri ile müşteriler, satış departmanları, pazar araştırma ve sektör uzmanları işbirliği içinde yürütür. Bu bilgiler, projeye temel yaklaşımı planlamak ve ekonomik, iş gücü ve teknik alanlarda fizibilite çalışması yapmak için kullanılır.

Planlama aşaması, kalite güvence gereksinimlerini planlamayı ve proje ile ilgili riskleri tanımlamayı da içerir. Teknik fizibilite çalışmasının sonucu, projeyi başarıyla uygulamak için izlenebilecek farklı teknik yaklaşımları tanımlamaktır.

Bu aşama aşağıdaki adımları içerebilir:
- Proje kapsamını belirlemek.
- Potansiyel riskleri, kısıtlamaları ve kaynakları tanımlamak.
- Proje planı oluşturmak (takvimler, kilometre taşları ve bütçe tahminleri dahil).
- Kullanıcı araştırması yaparak kullanıcı ihtiyaçlarını ve beklentilerini anlamak.

### Gereksinim Tanımlaması

Gereksinim analizi tamamlandıktan sonra, sonraki adım ürün gereksinimlerini net bir şekilde tanımlamak ve müşteriden veya pazar analizcilerinden onay almaktır. Bu, Yazılım Gereksinim Belgesi (SRS) aracılığıyla yapılır ve proje yaşam döngüsü boyunca tüm ürün gereksinimlerini içerir.

Bu aşama aşağıdaki faaliyetleri içerebilir:
- Gereksinimlerin ve ihtiyaçların toplanması ve belgelenmesi.
- Paydaşlardan (son kullanıcılar, müşteriler, vb.) spesifikasyonların toplanması.
- Gereksinimlerin fizibilite analizi.
- Gereksinimlerin önceliklendirilmesi ve onaylanması.

### Tasarım

Yazılım Gereksinim Belgesi, ürün mimarlarının ürün için en iyi mimariyi tasarlamak üzere temelini oluşturur. Yazılım Gereksinim Belgesinde tanımlanan gereksinimlere dayanarak, genellikle birden fazla ürün mimarisi tasarım çözümü önerilir ve Tasarım Belgesi Özellikleri (DDS) belgesinde belgelenir.

Tasarım Belgesi Özellikleri, tüm anahtar paydaşlar tarafından gözden geçirilir ve ürün için en iyi tasarım çözümü, risk değerlendirmesi, ürün sağlamlığı, tasarım modülerliği, bütçe ve zaman kısıtlamaları gibi çeşitli parametrelere dayanarak seçilir.

Tasarım yaklaşımı, ürün mimarisi modüllerini, dış ve üçüncü taraf modülleri (varsa) ile olan iletişimlerini ve veri akışlarını net bir şekilde tanımlar. Önerilen mimarinin tüm modüllerinin iç tasarımı, Tasarım Belgesi Özellikleri'nde en ince detaylarına kadar tanımlanmalıdır.

Bu aşamada, kullanıcı arayüzü (UI) ve kullanıcı deneyimi (UX) tasarımı da oluşturulur, bu da kullanıcıları etkilemek ve ürün kullanımını basitleştirmek için kritik öneme sahiptir.
- Gereksinimleri sistem özelliklerine dönüştürmek.
- Sistem mimarisi ve çerçevesi tasarımı.
- UX (Kullanıcı Deneyimi) ve UI (Kullanıcı Arayüzü) tasarımı.
- Uygun teknolojilerin, platformların ve araçların seçimi.

### Geliştirme

Bu SDLC aşamasında, ürünün gerçek geliştirilmesi ve inşası başlar. Programlama kodu, tasarım belgesi özelliklerine göre bu aşamada üretilir. Tasarım düzgün ve organize bir şekilde yapılmışsa, kod üretimi çok zor olmayacaktır.

Geliştiriciler, organizasyonları tarafından tanımlanan kodlama yönergelerine uymalı ve derleyiciler, hata ayıklayıcılar gibi programlama araçları kullanarak kodu üretmelidir. Yazılım geliştirme türüne bağlı olarak, C, C++, Pascal, Java, Javascript ve PHP gibi farklı yüksek seviyeli programlama dilleri kullanılır.
- Kod yazma.
- Tasarımı işlevsel yazılıma dönüştürme.
- Çeşitli bileşenleri entegre etme ve işbirliğini sağlama.

### Test Etme

Bu aşama genellikle tüm aşamaların bir alt kümesi olarak kabul edilir, çünkü modern SDLC modellerinde test etme faaliyetleri çoğu zaman tüm SDLC aşamalarını kapsar. Ancak, bu aşama ürün testi aşamasını ifade eder; burada ürünün hataları rapor edilir, izlenir, düzeltilir ve ürün kalite standartlarına ulaşana kadar yeniden test edilir.
- Yazılım gereksinimlerine uyumu doğrulamak.
- Hataları ve tutarsızlıkları düzeltmek ve doğrulamak.
- Çeşitli test yöntemlerini uygulamak (birim testi, entegrasyon testi, manuel test vb.).
- Yazılımın işlevselliğini, performansını, güvenliğini ve kullanılabilirliğini doğrulamak.

### Dağıtım

Ürün test edildikten ve dağıtıma hazır hale geldikten sonra, resmi olarak ilgili pazara sunulur. Bazen ürün dağıtımı, organizasyonun iş stratejisine göre aşamalı olarak yapılır. Ürün ilk olarak sınırlı bir segmentte yayımlanabilir ve gerçek bir iş ortamında test edilebilir (UAT – Kullanıcı Kabul Testi).

Ürün, geri bildirimlere göre hedef pazar segmentinde tavsiye edilen iyileştirmelerle birlikte veya tek başına yayımlanabilir.
- Yazılım başlatma ortamını hazırlamak.
- Yazılımı üretim ortamında kurmak ve uygulamak.
- Gerekirse son kullanıcıları eğitmek.
- Yazılımın performansını izlemek ve sorunsuz çalışmasını sağlamak.

### Bakım ve Destek

Yazılım dağıtıldıktan sonra, yazılımın sorun çıkmadan çalışmasını sağlamak ve kullanıcı ihtiyaçlarını karşılamak önemlidir. Bu, yazılımın zamanla çalışır, verimli ve ilgili kalmasını sağlamak için bakım ve destek gerektirir.
- Dağıtımdan sonra ortaya çıkan sorunları ve hataları çözmek.
- Kullanıcı geri bildirimlerine dayalı güncellemeler, düzeltmeler veya iyileştirmeler yapmak.
- Yazılımın çalışır, verimli ve ilgili kalmasını sağlamak.
- Güvenlik açıklarını ve uyumluluk sorunlarını ele almak.

### İnceleme ve Geribildirim

Son aşama, tüm SDLC sürecini gözden geçirmeyi ve gelecekteki yazılım sürümleri için nelerin iyileştirilebileceğini belirlemek amacıyla geribildirim toplamayı içerir. Bu aşama, yazılım geliştirme sürecinin sürekli olarak iyileştirilmesini ve kullanıcı ihtiyaçlarına göre şekillendirilmesini sağlamak için önemlidir.
- Paydaşlardan ve son kullanıcılardan geribildirim toplamak.
- Yazılım performansını analiz etmek ve iyileştirilmesi gereken alanları belirlemek.
- Sonraki yinelemeyi veya yazılım sürümünü planlamak.

Her bir aşama, özellikle çevik veya spiral modellerde yinelemeli olabilir, burada yazılım döngüler veya yinelemeler halinde geliştirilir. Kesin adımlar ve sıralamaları, seçilen SDLC modeline, organizasyonel süreçlere ve projenin doğasına bağlı olarak değişebilir. Ancak hedef aynıdır: Kullanıcı ihtiyaçlarını ve beklentilerini karşılayan kaliteli yazılımlar üretmek, en verimli şekilde mümkün olan en kısa sürede.

## SDLC'nin Önemi

- **Yapılandırılmış Süreç:** SDLC, yazılım geliştirme için yapılandırılmış bir yaklaşım sunarak, kritik adımların atlanmamasını sağlar.
- **Kalite Güvencesi:** Her SDLC aşamasının belirli çıktıları ve gözden geçirme süreçleri vardır, bu da daha iyi yazılım kalitesine yol açar.
- **Risk Yönetimi:** Olası sorunların veya risklerin erken tespiti, zamanında hafifletme yapılmasına olanak tanır.
- **Proje Yönetimi:** SDLC, proje ilerlemesini izleme, kaynak tahsisi yapma ve bütçelere uyma için net bir çerçeve sunar.
- **Paydaş İletişimi:** Net aşamalar ve sonuçlar tanımlayarak, paydaşlar sürecin ilerleyişi ve beklenen sonuçlar hakkında bilgilendirilir.
- **Verimlilik ve Maliyet Etkinliği:** Yazılım geliştirme sürecini sistematik bir şekilde ele alarak, israflar en aza indirilir ve verimlilik maksimuma çıkarılır.
- **Dokümantasyon:** SDLC'nin önemli bir parçası olan uygun dokümantasyon, bilginin korunmasını ve sistem detaylarının anlaşılmasını sağlar.

## Yaygın SDLC Modelleri:

### **Waterfall Modeli:**

- **Açıklama:** Her aşamanın bir sonraki aşama başlamadan önce tamamlanması gereken doğrusal ve ardışık bir yaklaşım. SDLC'nin ilk yaklaşımıdır.
- **Artıları:** Net yapı, anlaşılması kolay, iyi tanımlanmış aşamalar.
- **Eksileri:** Aşama tamamlandıktan sonra değişiklik yapmak zordur, karmaşık projeler için uygun değildir.

### **Lean**

- **Açıklama:** Üretimden türetilmiştir, kaynak optimizasyonuna ve müşteri değeri sunmaya odaklanır. Süreçten gereksiz "atıkları" ortadan kaldırmayı amaçlar.
- **Artıları:** Verimli kaynak kullanımı, değer teslimine odaklanır.
- **Eksileri:** Gerekli görevler "atık" olarak göz ardı edilebilir, doğru uygulamak için derin bir anlayış gerektirir.

### **Spiral Modeli:**

- **Açıklama:** Waterfall modelinin tasarım aşamasını, prototip oluşturmanın yinelemeli felsefesi ile birleştirir. Her spiralde risk değerlendirmesine odaklanır.
- **Artıları:** Risk yönetimine odaklanır, tasarım ve gereksinimlerde esneklik sağlar.
- **Eksileri:** Pahalı olabilir, risk değerlendirme uzmanlığı gerektirir.

### **Agile Modeli:**

- **Açıklama:** Yazılımı adım adım inşa eden, müşteri geri bildirimi ve hızlı yinelemelere odaklanan yinelemeli bir yazılım teslimatı yaklaşımıdır.
- **Artıları:** Esneklik, yinelemeli geri bildirim teşvik eder, müşteri katılımını destekler.
- **Eksileri:** Daha az öngörülebilirlik, geleneksel yöntemlere alışkın olanlar için zor olabilir.

### **Özellik Odaklı Geliştirme (FDD)**

- **Açıklama:** Özellik listeleri tarafından yönlendirilen yinelemeli ve artımlı bir yazılım geliştirme sürecidir.
- **Artıları:** Somut, müşteri değeri taşıyan fonksiyonlar inşa etmeye odaklanır.
- **Eksileri:** Diğer Çevik yöntemlere göre daha az esnektir, ayrıntılı dokümantasyon gerektirir.

### **Extreme Programming (XP)**

- **Açıklama:** Müşteri memnuniyetini vurgulayan, kısa geliştirme döngülerinde sık sık "yayınlar" yapan bir Çevik çerçevesidir.
- **Artıları:** Kod kalitesine odaklanır, müşteri katılımını teşvik eder.
- **Eksileri:** Kapsamlı müşteri katılımı gerektirir, geliştiriciler için yoğun olabilir.

### **Kanban:**

- **Açıklama:** Süreç yönetimine görsel bir yaklaşım, zamanında teslimata vurgu yapar ve "atık" ortadan kaldırılmaya çalışılır.
- **Artıları:** Esneklik, sürekli teslimat, görsel doğası tıkanıklıkları tanımlamaya yardımcı olur.
- **Eksileri:** Daha az yapılandırılmıştır, doğru yönetilmezse kapsam kayması olabilir.

### **Scrum:**

- **Açıklama:** Çalışmayı "Sprint" adı verilen döngülere ayıran, genellikle 2-4 hafta süren bir Çevik metodolojidir.
- **Artıları:** Düzenli ürün teslimatları, yüksek görünürlük, uyum sağlama.
- **Eksileri:** Deneyimli ekip üyeleri gerektirir, kapsam bazen çok esnek olabilir.

Sonuç olarak, SDLC çerçevesinin seçimi, projenin doğasına, organizasyonel tercihlere, ekip büyüklüğüne, proje kapsamına ve diğer faktörlere bağlıdır. Nihai hedef, kullanıcı beklentilerini karşılayan kaliteli yazılımlar üretmek ve zaman ve bütçe çerçevesini koruyarak bunu en verimli şekilde yapmaktır.

## Alıştırmalar ve Görevler

