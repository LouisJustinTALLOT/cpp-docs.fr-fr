---
title: "R&#232;gles et limitations pour dllimport/dllexport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dllexport (attribut) (C++)"
  - "dllexport (attribut) (C++), limitations et règles"
  - "dllimport (attribut) (C++), limitations et règles"
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# R&#232;gles et limitations pour dllimport/dllexport
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Section spécifique à Microsoft**  
  
-   Si vous déclarez une fonction sans l'attribut **dllimport** ou `dllexport`, elle n'est pas considérée comme faisant partie de l'interface DLL.  Par conséquent, la définition de la fonction doit être présente dans ce module ou dans un autre module du même programme.  Pour que la fonction fasse partie de l'interface DLL, vous devez déclarer la définition de la fonction dans l'autre module en tant que `dllexport`.  Sinon, une erreur de l'Éditeur de liens est générée lorsque le client est construit.  
  
-   Si un seul module de votre programme contient des déclarations **dllimport** et `dllexport` pour une même fonction, l'attribut `dllexport` est prioritaire sur l'attribut **dllimport**.  Toutefois, un avertissement du compilateur est généré.  Par exemple :  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllExport void func1( void );   /* Warning; dllexport */  
                                       /* takes precedence. */  
  
    ```  
  
-   Vous ne pouvez pas initialiser un pointeur de données statiques avec l'adresse d'un objet de données déclaré avec l'attribut **dllimport**.  Par exemple, le code suivant génère des erreurs :  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport int i;  
       .  
       .  
       .  
       int *pi = &i;                           /* Error */  
  
       void func2()  
       {  
          static int *pi = &i;                   /* Error */  
       }  
  
    ```  
  
-   L'initialisation d'un pointeur de fonction statique avec l'adresse d'une fonction déclarée avec **dllimport** définit le pointeur sur l'adresse de la conversion de code d'importation de la DLL \(stub de code qui transfère un contrôle à la fonction\) plutôt que l'adresse de la fonction.  Cette assignation ne génère pas de message d'erreur :  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void   
       .  
       .  
       .  
       static void ( *pf )( void ) = &func1;   /* No Error */  
  
       void func2()  
       {  
          static void ( *pf )( void ) = &func1;  /* No Error */  
       }  
  
    ```  
  
-   Comme un programme qui inclut l'attribut `dllexport` dans la déclaration d'un objet doit fournir la définition de cet objet, vous pouvez initialiser un pointeur de fonction statique global ou local avec l'adresse d'une fonction `dllexport`.  De même, vous pouvez initialiser un pointeur de données statiques global ou local avec l'adresse d'un objet de données `dllexport`.  Par exemple :  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllImport int i;  
  
       DllExport void func1( void );  
       DllExport int i;  
       .  
       .  
       .  
       int *pi = &i;                            /* Okay */  
       static void ( *pf )( void ) = &func1;    /* Okay */  
  
       void func2()  
       {  
          static int *pi = i;                     /* Okay */  
          static void ( *pf )( void ) = &func1;   /* Okay */  
       }  
  
    ```  
  
 **FIN de la section spécifique à Microsoft**  
  
## Voir aussi  
 [Fonctions d'importation et d'exportation de DLL](../c-language/dll-import-and-export-functions.md)