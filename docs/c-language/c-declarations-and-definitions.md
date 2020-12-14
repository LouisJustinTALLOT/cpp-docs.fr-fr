---
description: 'En savoir plus sur : déclarations et définitions C'
title: Déclarations et définitions C
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: dac53ac203c8e58e3af87e4869983c0443ffb092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254311"
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
