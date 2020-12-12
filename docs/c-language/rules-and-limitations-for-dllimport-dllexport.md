---
description: 'En savoir plus sur : règles et limitations pour DllImport/dllexport'
title: Règles et limitations pour dllimport-dllexport
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: 6d7de92b7d58eacc9334859a865e0e1456fffcb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292882"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Règles et limitations pour dllimport/dllexport

**Spécifique à Microsoft**

- Si vous déclarez une fonction sans **`dllimport`** l' `dllexport` attribut ou, la fonction n’est pas considérée comme faisant partie de l’interface dll. Par conséquent, la définition de la fonction doit être présente dans ce module ou dans un autre module du même programme. Pour que la fonction fasse partie de l'interface DLL, vous devez déclarer la définition de la fonction dans l'autre module en tant que `dllexport`. Sinon, une erreur de l'Éditeur de liens est générée lorsque le client est construit.

- Si un seul module de votre programme contient **`dllimport`** des `dllexport` déclarations et pour la même fonction, l' `dllexport` attribut est prioritaire sur l' **`dllimport`** attribut. Toutefois, un avertissement du compilateur est généré. Par exemple :

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Vous ne pouvez pas initialiser un pointeur de données statiques avec l’adresse d’un objet de données déclaré avec l' **`dllimport`** attribut. Par exemple, le code suivant génère des erreurs :

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

- L’initialisation d’un pointeur de fonction statique avec l’adresse d’une fonction déclarée avec **`dllimport`** définit le pointeur vers l’adresse du thunk d’importation de dll (un stub de code qui transfère le contrôle à la fonction) plutôt que l’adresse de la fonction. Cette assignation ne génère pas de message d'erreur :

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

- Comme un programme qui inclut l'attribut `dllexport` dans la déclaration d'un objet doit fournir la définition de cet objet, vous pouvez initialiser un pointeur de fonction statique global ou local avec l'adresse d'une fonction `dllexport`. De même, vous pouvez initialiser un pointeur de données statiques global ou local avec l'adresse d'un objet de données `dllexport`. Par exemple :

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Fonctions d’importation et d’exportation de DLL](../c-language/dll-import-and-export-functions.md)
