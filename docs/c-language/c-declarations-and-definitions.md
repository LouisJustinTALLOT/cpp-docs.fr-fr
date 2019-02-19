---
title: Déclarations et définitions C
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: 3be9cd72e9f4dbad4d279cc1bb65dfb92a61cd42
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150517"
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
