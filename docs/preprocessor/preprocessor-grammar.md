---
title: Syntaxe du préprocesseur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d14a3e00e18a2d3ac69dd472ac4056a379ada224
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843364"
---
# <a name="preprocessor-grammar"></a>Syntaxe du préprocesseur
**#define***identificateur* *chaîne de jeton*opt    
  
 *#* **définir***identificateur*[**(** *identificateur*opt **,** *...*  **,** *identificateur*opt **)**] *chaîne de jeton*opt  
  
 **défini (***identificateur* **)**   
  
 **défini***identificateur*   
  
 `#include` **«***spécification de chemin d’accès***»**  
  
 `#include` **\<***spécification de chemin d’accès***>**  
  
 **#line**  *digit-sequence*  **"** *filename* **"** opt  
  
 *#* **undef***identificateur*  
  
 **#error***chaîne de jeton*   
  
 **#pragma***chaîne de jeton*   
  
 *conditionnel* :  
 *If-partie elif-parties*opt*partie « else »* opt*endif en ligne*  
  
 *If-partie* :  
 *if-linetext*  
  
 *If-ligne* :  
 **#if**  *constant-expression*  
  
 **#ifdef***identificateur*   
  
 **#ifndef***identificateur*   
  
 *parties d’elif* :  
 *texte de la ligne d’elif*  
  
 *texte de ligne elif elif-parties*  
  
 *ligne elif* :  
 **#elif**  *constant-expression*  
  
 *partie « else »* :  
 *else-linetext*  
  
 *ligne Else* :  
 `#else`  
  
 *ligne endif* :  
 `#endif`  
  
 *séquence de chiffres* :  
 *digit*  
  
 *digit-sequence digit*  
  
 *chiffre* : un des  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *chaîne de jeton* :  
 Chaîne de jetons  
  
 *jeton* :  
 *keyword*  
  
 *identifier*  
  
 *constant*  
  
 *operator*  
  
 `punctuator`  
  
 *nom de fichier* :  
 Nom de fichier du système d'exploitation conforme  
  
 *spécification de chemin d’accès* :  
 Chemin d’accès de fichier conforme  
  
 *texte* :  
 Toute séquence de texte  
  
> [!NOTE]
>  Les éléments non terminaux suivants sont développés dans les [Conventions lexicales](../cpp/lexical-conventions.md) section de la *référence du langage C++*: `constant`, `constant` - *expression* , *identificateur*, *mot clé*, `operator`, et `punctuator`.  
  
## <a name="see-also"></a>Voir aussi  
 [Résumé de la grammaire (C/C++)](../preprocessor/grammar-summary-c-cpp.md)