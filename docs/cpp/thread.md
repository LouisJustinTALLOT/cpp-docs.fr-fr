---
description: 'En savoir plus sur : thread'
title: thread
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: 7b83686b6641585e7e7af334a6127c71a9171610
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164703"
---
# <a name="thread"></a>thread

**Spécifique à Microsoft**

Le **`thread`** modificateur de classe de stockage étendu est utilisé pour déclarer une variable locale de thread. Pour l’équivalent portable en C++ 11 et versions ultérieures, utilisez le spécificateur de classe de stockage [thread_local](../cpp/storage-classes-cpp.md#thread_local) pour le code portable. Sur Windows **`thread_local`** est implémenté avec **`__declspec(thread)`** .

## <a name="syntax"></a>Syntaxe

**`__declspec(thread)`***déclarateur*

## <a name="remarks"></a>Notes

Le stockage local des threads (TLS) est le mécanisme par lequel chaque thread d’un processus multithread alloue de l’espace de stockage pour les données spécifiques aux threads. Dans les programmes multithread standard, les données sont partagées entre tous les threads d’un processus donné, alors que le stockage local des threads est le mécanisme d’allocation des données par thread. Pour une description complète des threads, consultez [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Les déclarations de variables locales de thread doivent utiliser la [syntaxe d’attribut étendu](../cpp/declspec.md) et le **`__declspec`** mot clé avec le **`thread`** mot clé. Par exemple, le code suivant déclare une variable locale de thread entière et lui affecte une valeur initiale :

```cpp
__declspec( thread ) int tls_i = 1;
```

Lorsque vous utilisez des variables de thread local dans des bibliothèques chargées dynamiquement, vous devez être conscient des facteurs qui peuvent provoquer l’échec de l’initialisation d’une variable locale de thread :

1. Si la variable est initialisée avec un appel de fonction (y compris des constructeurs), cette fonction sera uniquement appelée pour le thread qui a provoqué le chargement du fichier binaire/DLL dans le processus, et pour les threads qui ont démarré après le chargement du fichier binaire/DLL. Les fonctions d’initialisation ne sont pas appelées pour tout autre thread déjà en cours d’exécution lors du chargement de la DLL. L’initialisation dynamique se produit sur l’appel DllMain pour DLL_THREAD_ATTACH, mais la DLL n’obtient jamais ce message si la DLL n’est pas dans le processus au démarrage du thread.

1. Les variables locales de thread qui sont initialisées statiquement avec des valeurs constantes sont généralement initialisées correctement sur tous les threads. Toutefois, à compter du 2017 décembre, il existe un problème de conformité connu dans le compilateur Microsoft C++, selon lequel les **`constexpr`** variables reçoivent des variables dynamiques plutôt qu’une initialisation statique.

   Remarque : ces deux problèmes sont censés être résolus dans les mises à jour ultérieures du compilateur.

En outre, vous devez respecter ces instructions lors de la déclaration des variables et des objets locaux de thread :

- Vous pouvez appliquer l' **`thread`** attribut uniquement aux déclarations et aux définitions de classe et de données ; **`thread`** ne peut pas être utilisé sur des définitions ou des déclarations de fonction.

- Vous pouvez spécifier l' **`thread`** attribut uniquement sur les éléments de données ayant une durée de stockage statique. Cela comprend les objets de données globaux (à la fois **`static`** et **`extern`** ), les objets statiques locaux et les membres de données statiques des classes. Vous ne pouvez pas déclarer d’objets de données automatiques avec l' **`thread`** attribut.

- Vous devez utiliser l' **`thread`** attribut pour la déclaration et la définition d’un objet local de thread, que la déclaration et la définition se produisent dans le même fichier ou dans des fichiers distincts.

- Vous ne pouvez pas utiliser l' **`thread`** attribut en tant que modificateur de type.

- Étant donné que la déclaration d’objets qui utilisent l' **`thread`** attribut est autorisée, ces deux exemples sont sémantiquement équivalents :

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- Standard C permet l’initialisation d’un objet ou d’une variable à l’aide d’une expression impliquant une référence à elle-même, mais uniquement pour les objets non statiques. Bien que C++ autorise normalement l’initialisation dynamique d’un objet avec une expression impliquant une référence à lui-même, ce type d’initialisation n’est pas autorisé avec les objets locaux de thread. Par exemple :

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Une **`sizeof`** expression qui comprend l’objet initialisé ne constitue pas une référence à elle-même et est autorisée en C et C++.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Stockage local des threads (TLS)](../parallel/thread-local-storage-tls.md)
