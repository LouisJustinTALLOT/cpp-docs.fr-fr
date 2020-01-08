---
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
ms.openlocfilehash: cc21602764a9a3c2584bdd7da62c75974ffdd5fb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301286"
---
# <a name="thread"></a>thread

**Section spécifique à Microsoft**

Le modificateur de classe de stockage étendu de **thread** est utilisé pour déclarer une variable locale de thread. Pour l’équivalent portable en C++ 11 et versions ultérieures, utilisez le spécificateur de classe de stockage [thread_local](../cpp/storage-classes-cpp.md#thread_local) pour le code portable. Sur Windows **thread_local** est implémenté avec **__declspec (thread)** .

## <a name="syntax"></a>Syntaxe

*déclarateur* **__declspec (thread)**

## <a name="remarks"></a>Notes

Le stockage local des threads (TLS) est le mécanisme par lequel chaque thread d’un processus multithread alloue de l’espace de stockage pour les données spécifiques aux threads. Dans les programmes multithread standard, les données sont partagées entre tous les threads d’un processus donné, alors que le stockage local des threads est le mécanisme d’allocation des données par thread. Pour une description complète des threads, consultez [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Les déclarations de variables locales de thread doivent utiliser la [syntaxe d’attribut étendu](../cpp/declspec.md) et le mot clé **__declspec** avec le mot clé **thread** . Par exemple, le code suivant déclare une variable locale de thread entière et lui affecte une valeur initiale :

```cpp
__declspec( thread ) int tls_i = 1;
```

Lorsque vous utilisez des variables de thread local dans des bibliothèques chargées dynamiquement, vous devez être conscient des facteurs qui peuvent provoquer l’échec de l’initialisation d’une variable locale de thread :

1. Si la variable est initialisée avec un appel de fonction (y compris des constructeurs), cette fonction sera uniquement appelée pour le thread qui a provoqué le chargement du fichier binaire/DLL dans le processus, et pour les threads qui ont démarré après le chargement du fichier binaire/DLL. Les fonctions d’initialisation ne sont pas appelées pour tout autre thread déjà en cours d’exécution lors du chargement de la DLL. L’initialisation dynamique se produit sur l’appel DllMain pour DLL_THREAD_ATTACH, mais la DLL n’obtient jamais ce message si la DLL n’est pas dans le processus au démarrage du thread.

1. Les variables locales de thread qui sont initialisées statiquement avec des valeurs constantes sont généralement initialisées correctement sur tous les threads. Toutefois, depuis décembre 2017, il existe un problème de conformité connu dans le compilateur Microsoft C++ , selon lequel les variables **constexpr** reçoivent une initialisation dynamique plutôt qu’une initialisation statique.

   Remarque : ces deux problèmes sont censés être résolus dans les mises à jour ultérieures du compilateur.

En outre, vous devez respecter ces instructions lors de la déclaration des variables et des objets locaux de thread :

- Vous pouvez appliquer l’attribut de **thread** uniquement aux déclarations et aux définitions de classe et de données ; le **thread** ne peut pas être utilisé sur les déclarations ou les définitions de fonctions.

- Vous pouvez spécifier l’attribut de **thread** uniquement sur les éléments de données ayant une durée de stockage statique. Cela comprend les objets de données globaux ( **statiques** et **externes**), les objets statiques locaux et les membres de données statiques des classes. Vous ne pouvez pas déclarer d’objets de données automatiques avec l’attribut de **thread** .

- Vous devez utiliser l’attribut de **thread** pour la déclaration et la définition d’un objet local de thread, que la déclaration et la définition se produisent dans le même fichier ou dans des fichiers distincts.

- Vous ne pouvez pas utiliser l’attribut de **thread** en tant que modificateur de type.

- Étant donné que la déclaration d’objets qui utilisent l’attribut de **thread** est autorisée, ces deux exemples sont sémantiquement équivalents :

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

- Standard C permet l’initialisation d’un objet ou d’une variable à l’aide d’une expression impliquant une référence à elle-même, mais uniquement pour les objets non statiques. Bien C++ qu’il autorise normalement l’initialisation dynamique d’un objet avec une expression impliquant une référence à lui-même, ce type d’initialisation n’est pas autorisé avec les objets locaux de thread. Par exemple :

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Une expression **sizeof** qui comprend l’objet initialisé ne constitue pas une référence à elle-même et est autorisée en C et C++.

**Fin de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Stockage local des threads (TLS)](../parallel/thread-local-storage-tls.md)