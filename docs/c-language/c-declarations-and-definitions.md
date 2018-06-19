---
title: Définitions et déclarations C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c459999ab902a2498d4ffe4cc2d437a0a432b9b7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381563"
---
# <a name="c-declarations-and-definitions"></a>Déclarations et définitions C
Une déclaration établit une association entre une variable, une fonction ou un type particulier et ses attributs. [Vue d'ensemble des déclarations](../c-language/overview-of-declarations.md) donne la syntaxe ANSI pour le non terminal `declaration`. Une déclaration spécifie également où et quand un identificateur est accessible (liaison d'un identificateur). Consultez [Durée de vie, portée, visibilité, et liaison](../c-language/lifetime-scope-visibility-and-linkage.md) pour plus d'informations sur la liaison.  
  
 Une définition d'une variable établit les mêmes associations qu'une déclaration mais génère également un stockage à allouer pour la variable.  
  
 Par exemple, les fonctions `main`, `find` et `count` et les variables `var` et `val` sont définies dans un fichier source dans l'ordre suivant :  
  
```  
int main() {}  
  
int var = 0;  
double val[MAXVAL];  
char find( fileptr ) {}  
int count( double f ) {}  
```  
  
 Les variables `var` et `val` peuvent être utilisées dans les fonctions `find` et `count`. Aucune autre déclaration n'est requise. Mais ces noms ne sont pas visibles (sont inaccessibles) dans `main`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers sources et programmes sources](../c-language/source-files-and-source-programs.md)