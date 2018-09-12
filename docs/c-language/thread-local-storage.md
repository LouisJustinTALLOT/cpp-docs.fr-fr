---
title: Stockage local des threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92ad8d3543c8ad64ea90a422b39147c93c8e6465
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754746"
---
# <a name="thread-local-storage"></a>stockage local des threads
**Section spécifique à Microsoft**  
  
Le stockage local des threads (TLS) est le mécanisme par lequel chaque thread d’un processus multithread donné alloue de l’espace de stockage pour les données spécifiques aux threads. Dans les programmes multithread standard, les données sont partagées entre tous les threads d’un processus donné, alors que le stockage local des threads est le mécanisme d’allocation des données par thread. Pour une description complète des threads, consultez [Threads et processus](/windows/desktop/ProcThread/processes-and-threads) dans le kit SDK Windows.  
  
Le langage Microsoft C inclut l’attribut de classe de stockage étendu, le thread, utilisé avec le mot clé __declspec pour déclarer une variable locale de thread. Par exemple, le code suivant déclare une variable locale de thread entière et lui affecte une valeur initiale :  

```
__declspec( thread ) int tls_i = 1;  
```  
  
Ces instructions doivent être observées lors de la déclaration de variables et d’objets locaux statiques du thread :  
  
-   Les variables locales à un thread dont l’initialisation est dynamique sont initialisées seulement sur le thread qui provoque le chargement de la DLL, et sur les threads qui sont déjà en cours d’exécution dans le processus. Pour plus d’informations, consultez [thread](../cpp/thread.md).  
  
-   Vous pouvez appliquer l'attribut de thread uniquement aux déclarations et aux définitions de données. Il ne peut pas être utilisé avec des définitions ou des déclarations de fonction. Par exemple, le code suivant génère une erreur de compilation :  

    ```C
    #define Thread   __declspec( thread )  
    Thread void func();      /* Error */  
    ```  
  
-   Vous pouvez spécifier l'attribut de thread uniquement pour les éléments de données ayant une durée de stockage statique. Cela inclut des données globales (statiques et externes) et des données statiques locales. Vous ne pouvez pas déclarer de données automatiques à l'aide de l'attribut de thread. Par exemple, le code suivant génère des erreurs de compilation :  
  
    ```C
    #define Thread   __declspec( thread )  
    void func1()  
    {  
        Thread int tls_i;            /* Error */  
    }  
  
    int func2( Thread int tls_i )    /* Error */  
    {  
       return tls_i;  
    }  
    ```  
  
-   Vous devez utiliser l'attribut de thread pour la déclaration et la définition de données locales de thread, que la déclaration et la définition se produisent dans le même fichier ou dans des fichiers séparés. Par exemple, le code suivant génère une erreur :  
  
    ```C
    #define Thread   __declspec( thread )  
    extern int tls_i;     /* This generates an error, because the   */  
    int Thread tls_i;     /* declaration and the definition differ. */  
    ```  
  
-   Vous ne pouvez pas utiliser l'attribut de thread en tant que modificateur de type. Par exemple, le code suivant génère une erreur de compilation :  
  
    ```C
    char *ch __declspec( thread );      /* Error */  
    ```  
  
-   L'adresse d'une variable locale d'un thread n'est pas considérée comme étant constante, et toute expression impliquant une telle adresse n'est pas considérée comme une expression constante. Cela signifie que vous ne pouvez pas utiliser l'adresse d'une variable locale de thread comme initialiseur d'un pointeur. Par exemple, le compilateur signale le code suivant en tant qu'erreur :  
  
    ```C
    #define Thread   __declspec( thread )  
    Thread int tls_i;  
    int *p = &tls_i;      /* Error */  
    ```  
  
-   Le langage C permet l'initialisation d'une variable à l'aide d'une expression impliquant une auto-référence, mais uniquement pour les objets d'étendue non statique. Exemple :  
  
    ```C
    #define Thread   __declspec( thread )  
    Thread int tls_i = tls_i;             /* Error */  
    int j = j;                            /* Error */  
    Thread int tls_i = sizeof( tls_i )    /* Okay  */  
    ```  
  
     Notez qu'une expression sizeof qui inclut la variable initialisée ne constitue pas une référence à elle-même et est autorisée.  
  
-   L'utilisation de **__declspec(thread)** peut perturber le [chargement différé](../build/reference/linker-support-for-delay-loaded-dlls.md) des importations de DLL **.**  
  
Pour plus d'informations sur l'utilisation de l'attribut de thread, consultez [Rubriques de multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
[Attributs étendus de classe de stockage C](../c-language/c-extended-storage-class-attributes.md)