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
ms.openlocfilehash: 59a1af8a7eb73207f84ddf2194d5fe9e77d7d46a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221962"
---
# <a name="thread"></a>thread

**Section spécifique à Microsoft**

Le **thread** modificateur de classe de stockage étendu est utilisé pour déclarer une variable locale de thread. Pour la fonction portable équivalente dans C ++ 11 et versions ultérieure, utilisez le [thread_local](../cpp/storage-classes-cpp.md#thread_local) spécificateur de classe de stockage pour du code portable. Sur Windows `thread_local` est implémentée avec **__declspec (thread)**.

## <a name="syntax"></a>Syntaxe

> **__declspec( thread )** *declarator*

## <a name="remarks"></a>Notes

Le stockage local des threads (TLS) est le mécanisme par lequel chaque thread d’un processus multithread alloue de l’espace de stockage pour les données spécifiques aux threads. Dans les programmes multithread standard, les données sont partagées entre tous les threads d’un processus donné, alors que le stockage local des threads est le mécanisme d’allocation des données par thread. Pour obtenir une description complète des threads, consultez [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Les déclarations de variables locales de thread doivent utiliser [étendu de syntaxe d’attribut](../cpp/declspec.md) et le **__declspec** mot clé avec le **thread** mot clé. Par exemple, le code suivant déclare une variable locale de thread entière et lui affecte une valeur initiale :

```cpp
__declspec( thread ) int tls_i = 1;
```

Lorsque vous utilisez des variables locales de thread dans les bibliothèques chargées dynamiquement, vous devez être conscient des facteurs qui peuvent provoquer une variable de thread local ne pas être initialisé correctement :

1. Si la variable est initialisée avec un appel de fonction (y compris les constructeurs), cette fonction sera uniquement être appelée pour le thread qui a provoqué la binaire/DLL à charger dans le processus et pour les threads qui ont démarré après que le fichier binaire/DLL a été chargée. Les fonctions d’initialisation ne sont pas appelées pour n’importe quel autre thread qui a été déjà en cours d’exécution lors du chargement de la DLL. L’initialisation dynamique produit sur l’appel de DllMain pour DLL_THREAD_ATTACH, mais la DLL jamais Obtient le message si la DLL n’est pas dans le processus lorsque le thread ne démarre.

1. Les variables locales de thread qui sont initialisés de façon statique avec des valeurs constantes sont généralement initialisés correctement sur tous les threads. Toutefois, à compter de décembre 2017 il existe un problème de conformité connus dans Microsoft C++ compilateur par lequel les variables de constexpr de réception dynamique au lieu de l’initialisation statique.

   Remarque : Ces deux problèmes sont supposées être corrigé dans les prochaines mises à jour du compilateur.

En outre, vous devez respecter ces indications lorsque vous déclarez des variables et objets locaux de thread :

- Vous pouvez appliquer le **thread** attribut uniquement à la classe et données déclarations et définitions ; **thread** ne peut pas être utilisé sur des définitions ou déclarations de fonction.

- Vous pouvez spécifier le **thread** attribut uniquement sur les éléments de données avec une durée de stockage statique. Cela inclut les objets de données globaux (à la fois **statique** et **extern**), les objets statiques locaux et les données membres statiques des classes. Vous ne pouvez pas déclarer des objets de données automatiques avec le **thread** attribut.

- Vous devez utiliser le **thread** d’attribut pour la déclaration et la définition d’un objet local de thread, que la déclaration et la définition se produisent dans le même fichier ou des fichiers distincts.

- Vous ne pouvez pas utiliser le **thread** attribut sous la forme d’un modificateur de type.

- Étant donné que la déclaration d’objets qui utilisent le **thread** attribut est autorisé, ces deux exemples sont sémantiquement équivalentes :

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

- Le langage C standard permet l'initialisation d'un objet ou d'une variable à l'aide d'une expression impliquant une auto-référence, mais uniquement pour les objets d'étendue non statique. Même si C++ admet normalement l’initialisation dynamique d’un objet à l’aide d’une référence impliquant une auto-référence, ce type d’initialisation n’est pas permis avec les objets locaux de thread. Exemple :

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Notez qu’un **sizeof** expression qui inclut l’objet initialisé ne constitue pas une référence à lui-même et est autorisée en C et C++.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Stockage local des threads (TLS)](../parallel/thread-local-storage-tls.md)