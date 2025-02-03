# Requirements

In this topic we'll explore the concepts of software requirements - what they are, why they're important, and how to write them.

## Learning Outcomes

By the end of this topic you should be able to:


## What are Software Requirements?

Software requirements are the *functional* and *non-functional* requirements that define the scope of a software project. Requirements are a key part of the software development process, and they're important to get right. Requirements describe the expected behavior of the software, and they're used to guide the development process.

**Functional** requirements describe what the software should do. They're the features and functionality that the software should have. For example, a functional requirement might be:
- `the software should allow users to log in`;
- `the software should allow users to change their password`;
- `the software should allow users to reset their password`.

**Non-functional** requirements describe how the software should do it. They're the constraints and limitations that the software should have (including technical requirement). For example, a non-functional requirement might be:
- `the software should be able to handle 1000 concurrent users`;
- `the software should use bcrypt to hash passwords`;
- `the software should be able to run on Linux, Windows, and macOS`.

Requirements can be described in different levels of detail. For example, a high-level requirement might be
- `the software should allow users to log in`.

A more detailed requirement might be
- `the software should allow users to log in with their email address and password`.

A very detailed requirement might be
- `the software should allow users to log in with their email address and password, and it should use bcrypt to hash the password before storing it in the database`.

### User Requirements vs System Requirements

We can also categorize requirements as *user* requirements or *system* requirements.

**User requirements** describe what the user wants the software to do. Users requirements can be written using the user's own words with possible diagrams and pictures about what system should do or look like. It would be written in user's perspective.

**System requirements** describe what the system needs to do to meet the user requirements.This is more detailed description about system functionality, interfaces and performance and what exactly would be needed to meet user requirements. It is more technical description of what system should do.

> There are lot of different ways to categorize or describe requirements. The most important thing is to write them down and make sure that they are clear and understandable.
>
> We should always validate our requirements with our users and stakeholders. We should always make sure that we understand what they want and need, and that they understand what we're building.

## How to develop Software Requirements?

During the development of requirements, information is collected about the software to be created and the existing (working in real life) system.

User requirements and system requirements are created using collected information. The following activities are performed for this purpose:
- documents related to the field are consulted;
- communicating with the interest group;
- similar systems are studied.

### Stakeholders

Stakeholders are the people who have an interest in the software. They can be:
- users;
- customers;
- managers;
- business analysts;
- ...


## Exercises

# Gereksinimler

Bu konuda, yazılım gereksinimlerinin ne olduğunu, neden önemli olduklarını ve nasıl yazıldıklarını keşfedeceğiz.

## Öğrenme Çıktıları

Bu konuyu tamamladıktan sonra şunları yapabileceksiniz:

## Yazılım Gereksinimleri Nedir?

Yazılım gereksinimleri, bir yazılım projesinin kapsamını tanımlayan *fonksiyonel* ve *fonksiyonel olmayan* gereksinimlerdir. Gereksinimler, yazılım geliştirme sürecinin önemli bir parçasıdır ve doğru şekilde ele alınması gereklidir. Gereksinimler, yazılımın beklenen davranışını tanımlar ve geliştirme sürecine yön vermek için kullanılır.

**Fonksiyonel** gereksinimler, yazılımın ne yapması gerektiğini tanımlar. Yazılımın sahip olması gereken özellikler ve işlevselliklerdir. Örneğin, bir fonksiyonel gereksinim şu şekilde olabilir:
- `yazılım, kullanıcıların giriş yapmasına izin vermelidir`;
- `yazılım, kullanıcıların şifrelerini değiştirmelerine izin vermelidir`;
- `yazılım, kullanıcıların şifrelerini sıfırlamalarına izin vermelidir`.

**Fonksiyonel olmayan** gereksinimler, yazılımın bunu nasıl yapması gerektiğini tanımlar. Yazılımın sahip olması gereken kısıtlamalar ve sınırlamalardır (teknik gereksinimler de dahil). Örneğin, bir fonksiyonel olmayan gereksinim şu şekilde olabilir:
- `yazılım, 1000 eşzamanlı kullanıcıyı desteklemelidir`;
- `yazılım, şifreleri hash'lemek için bcrypt kullanmalıdır`;
- `yazılım, Linux, Windows ve macOS üzerinde çalışabilmelidir`.

Gereksinimler, farklı detay seviyelerinde tanımlanabilir. Örneğin, yüksek seviyeli bir gereksinim şu şekilde olabilir:
- `yazılım, kullanıcıların giriş yapmasına izin vermelidir`.

Daha detaylı bir gereksinim şu şekilde olabilir:
- `yazılım, kullanıcıların e-posta adresi ve şifreleri ile giriş yapmalarına izin vermelidir`.

Çok detaylı bir gereksinim şu şekilde olabilir:
- `yazılım, kullanıcıların e-posta adresi ve şifreleri ile giriş yapmalarına izin vermelidir ve şifreyi veritabanına kaydetmeden önce bcrypt kullanarak hash'lemelidir`.

### Kullanıcı Gereksinimleri ve Sistem Gereksinimleri

Gereksinimleri *kullanıcı* gereksinimleri veya *sistem* gereksinimleri olarak da kategorize edebiliriz.

**Kullanıcı gereksinimleri**, kullanıcının yazılımın ne yapmasını istediğini tanımlar. Kullanıcı gereksinimleri, kullanıcının kendi kelimeleriyle ve sistemin ne yapması veya nasıl görünmesi gerektiğini gösteren diyagramlar ve resimlerle yazılabilir. Kullanıcının perspektifinden yazılmalıdır.

**Sistem gereksinimleri**, sistemin kullanıcı gereksinimlerini karşılamak için ne yapması gerektiğini tanımlar. Bu, sistemin işlevselliği, arabirimleri ve performansıyla ilgili daha ayrıntılı bir açıklamadır ve kullanıcı gereksinimlerini karşılamak için tam olarak ne gerektiğini tanımlar. Bu, sistemin ne yapması gerektiği ile ilgili daha teknik bir açıklamadır.

> Gereksinimleri kategorize etmenin veya açıklamanın birçok farklı yolu vardır. En önemli şey, bunları yazmak ve net ve anlaşılır olduklarından emin olmaktır.
>
> Gereksinimlerimizi her zaman kullanıcılarımız ve paydaşlarımızla doğrulamalıyız. Onların ne istediklerini ve ihtiyaç duyduklarını anlamalı ve biz ne inşa ediyorsak, bunun ne olduğunu anlamalarını sağlamalıyız.

## Yazılım Gereksinimleri Nasıl Geliştirilir?

Gereksinimlerin geliştirilmesi sırasında, yapılacak yazılım ve mevcut (gerçek dünyada çalışan) sistemle ilgili bilgi toplanır.

Kullanıcı gereksinimleri ve sistem gereksinimleri, toplanan bilgiler kullanılarak oluşturulur. Bunun için aşağıdaki faaliyetler yapılır:
- ilgili alanla ilgili belgeler incelenir;
- ilgilenen taraflarla iletişim kurulur;
- benzer sistemler incelenir.

### Paydaşlar

Paydaşlar, yazılımla ilgisi olan kişilerdir. Bunlar şunlar olabilir:
- kullanıcılar;
- müşteriler;
- yöneticiler;
- iş analistleri;
- ...

