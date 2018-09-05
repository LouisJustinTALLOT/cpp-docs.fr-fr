---
title: Déclarateurs et déclarations de variable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a5ec2cf7984940421726dd0197dff4cf6d5ea0c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200357"
---
# <a name="declarators-and-variable-declarations"></a>Déclarateurs et déclarations de variable
Le reste de cette section décrit la forme et la signification des déclarations pour les types de variable répertoriés dans cette liste. Plus particulièrement, les sections restantes expliquent comment déclarer les éléments suivants :  
  
|Type de variable|Description|  
|----------------------|-----------------|  
|[Variables simples](../c-language/simple-variable-declarations.md)|Variables à valeur unique avec type intégral ou virgule flottante|  
|[Tableaux](../c-language/array-declarations.md)|Variables composées d’une collection d’éléments du même type|  
|[Pointeurs](../c-language/pointer-declarations.md)|Variables qui pointent vers d'autres variables et contiennent des emplacements de variables (sous la forme d'adresses) au lieu de valeurs|  
|[Variables d’énumération](../c-language/c-enumeration-declarations.md)|Variables simples avec type intégral qui contiennent une valeur d'un ensemble de constantes entières désignées|  
|[Structures](../c-language/structure-declarations.md)|Variables composées d’une collection de valeurs qui peuvent avoir des types différents|  
|[Unions](../c-language/union-declarations.md)|Variables composées de plusieurs valeurs de types différents qui occupent le même espace de stockage|  
  
 Un déclarateur est la partie d'une déclaration qui spécifie le nom qui doit être introduit dans le programme. Il peut inclure des modificateurs tels que <strong>\*</strong> (pointeur vers), et n’importe quel mot clé de convention d’appel Microsoft.  
  
 **Section spécifique à Microsoft**  
  
 Dans le déclarateur  
  
```  
__declspec(thread) char *var;  
```  
  
 `char` est le spécificateur de type, `__declspec(thread)` et `*` sont les modificateurs, et `var` est le nom de l'identificateur.  
  
 **FIN de la section spécifique à Microsoft**  
  
 Vous utilisez des déclarateurs pour déclarer des tableaux de valeurs, des pointeurs vers des valeurs et des fonctions qui retournent des valeurs d'un type spécifié. Les déclarateurs sont indiqués dans le tableau et les déclarations de pointeur sont décrites plus loin dans cette section.  
  
## <a name="syntax"></a>Syntaxe  
 *declarator* :  
 &nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*  
  
 *direct-declarator* :  
 &nbsp;&nbsp;*identifier*  
 &nbsp;&nbsp;**(**  *declarator*  **)**  
 &nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**  
 &nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**  
 &nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**  
  
 *pointer* :  
 &nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub>  
 &nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*  
  
 *type-qualifier-list* :  
 &nbsp;&nbsp;*type-qualifier*  
 &nbsp;&nbsp;*type-qualifier-list type-qualifier*  
  
> [!NOTE]
>  Consultez la syntaxe des *déclarations* dans la section [Vue d’ensemble des déclarations](../c-language/overview-of-declarations.md) ou [Résumé de syntaxe du langage C](../c-language/c-language-syntax-summary.md) pour la syntaxe qui référence un *déclarateur*.  
  
 Lorsqu'un déclarateur se compose d'un identificateur non modifié, l'élément déclaré a un type de base. Si un astérisque (<strong>\*</strong>) apparaît à gauche d’un identificateur, le type est remplacé par un type pointeur. Si l’identificateur est suivi de crochets (**[ ]**), le type est remplacé par un type tableau. Si l'identificateur est suivi de parenthèses, le type est remplacé par un type fonction. Pour plus d’informations sur l’interprétation de la priorité dans les déclarations, consultez [Interprétation de déclarateurs plus complexes](../c-language/interpreting-more-complex-declarators.md).  
  
 Chaque déclarateur déclare au moins un identificateur. Un déclarateur doit contenir un spécificateur de type afin que la déclaration soit complète. Le spécificateur de type indique le type des éléments d’un type tableau, le type d’objet adressé par un type pointeur ou le type de retour d’une fonction.  
  
 Les déclarations de [tableau](../c-language/array-declarations.md) et de [pointeur](../c-language/pointer-declarations.md) sont décrites plus en détail plus loin dans cette section. Les exemples suivants illustrent des formes simples de déclarateurs :  
  
```  
int list[20]; // Declares an array of 20 int values named list  
char *cp;     // Declares a pointer to a char value  
double func( void ); // Declares a function named func, with no   
                     // arguments, that returns a double value  
int *aptr[10] // Declares an array of 10 pointers  
```  
  
 **Section spécifique à Microsoft**  
  
 Le compilateur Microsoft C ne limite pas le nombre de déclarateurs pouvant modifier un type arithmétique, structure ou union. Le nombre est limité uniquement par la mémoire disponible.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations et types](../c-language/declarations-and-types.md)