---
title: Spécificateur extern de classe de stockage │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08a578514aaf6de4132bd856900b0ec31d31835c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388726"
---
# <a name="extern-storage-class-specifier"></a>Spécificateur extern de classe de stockage
Une variable déclarée avec le spécificateur de classe de stockage `extern` est une référence à une variable du même nom définie au niveau externe dans n'importe quel fichier source du programme. La déclaration interne `extern` est utilisée pour rendre la définition de variable au niveau externe visible dans le bloc. Sauf déclaration contraire au niveau externe, une variable déclarée avec le mot clé `extern` est visible uniquement dans le bloc dans lequel elle est déclarée.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre les déclarations aux niveaux interne et externe :  
  
```  
// extern_StorageClassSpecified.c  
#include <stdio.h>  
  
void other( void );  
  
int main()  
{  
    // Reference to i, defined below:   
    extern int i;  
  
    // Initial value is zero; a is visible only within main:   
    static int a;  
  
    // b is stored in a register, if possible:   
    register int b = 0;  
  
    // Default storage class is auto:   
    int c = 0;  
  
    // Values printed are 1, 0, 0, 0:   
    printf_s( "%d\n%d\n%d\n%d\n", i, a, b, c );  
    other();  
    return;  
}  
  
int i = 1;  
  
void other( void )  
{  
    // Address of global i assigned to pointer variable:  
    static int *external_i = &i;  
  
    // i is redefined; global i no longer visible:   
    int i = 16;  
  
    // This a is visible only within the other function:   
    static int a = 2;  
  
    a += 2;  
    // Values printed are 16, 4, and 1:  
    printf_s( "%d\n%d\n%d\n", i, a, *external_i );  
}  
```  
  
 Dans cet exemple, la variable `i` est définie au niveau externe avec la valeur initiale 1. Une déclaration `extern` dans la fonction `main` permet de déclarer une référence à `i` au niveau externe. La variable **static** `a` est initialisée à 0 par défaut, car l'initialiseur est omis. L'appel à `printf` imprime les valeurs 1, 0, 0 et 0.  
  
 Dans la fonction `other`, l'adresse de la variable globale `i` est utilisée pour initialiser la variable pointeur **static** `external_i`. Cela fonctionne, car la variable globale possède une durée de vie **static**, ce qui signifie que son adresse ne change pas pendant l'exécution du programme. Ensuite, la variable `i` est redéfinie comme variable locale avec la valeur initiale 16. Cette redéfinition n'affecte pas la valeur de `i` au niveau externe, qui est masqué par l'utilisation de son nom pour la variable locale. La valeur de `i` global est désormais accessible uniquement indirectement dans ce bloc, via le pointeur `external_i`. La tentative d'assigner l'adresse de la variable **auto** `i` à un pointeur échoue, car elle peut être différente à chaque entrée dans le bloc. La variable `a` est déclarée comme variable **static** et initialisé à 2. Ce `a` n'est pas en conflit avec le `a` dans `main`, car les variables **static** au niveau interne sont visibles uniquement dans le bloc dans lequel elles sont déclarées.  
  
 La variable `a` augmente de 2. Le résultat est donc 4. Si la fonction `other` était de nouveau appelée dans le même programme, la valeur initiale de `a` serait 4. Les variables **static** internes conservent leurs valeurs lorsque le programme s'arrête, puis entrent à nouveau dans le bloc dans lequel elles sont déclarées.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécificateurs de classe de stockage pour les déclarations de niveau interne](../c-language/storage-class-specifiers-for-internal-level-declarations.md)