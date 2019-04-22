---
title: Décoration de nom
ms.date: 09/05/2018
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: b916a73e0b8f86755384914fa85ef8a901e4a64c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041521"
---
# <a name="name-decoration"></a>Décoration de nom

La décoration de nom se rapporte généralement aux conventions d'affectation de noms C++, mais peut également s'appliquer à un certain nombre de cas du C. Par défaut, C++ utilise le nom de la fonction, les paramètres et le type de retour pour créer un nom d'éditeur de liens pour la fonction. Considérons la fonction suivante :

```
void CALLTYPE test(void)
```

Le tableau suivant montre le nom de l'éditeur de liens pour différentes conventions d'appel.

|Convention d'appel|extern "C" ou fichier .c|.cpp, .cxx ou /TP|
|------------------------|---------------------------|------------------------|
|Convention d'affectation de noms C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Convention d'affectation de noms Fastcall (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Convention d'affectation de noms Appel standard (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Convention d'affectation de noms Vectorcall (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Utilisez extern "C" pour appeler une fonction C à partir de C++. Extern "C" force l'utilisation de la convention d'affectation de noms C pour les fonctions C++ qui ne sont pas des fonctions de classe. N’oubliez pas de commutateurs du compilateur **TP** ou **/Tp**, qui indiquent au compilateur d’ignorer l’extension de nom de fichier et de compiler le fichier en tant que C ou C++, respectivement. Ces options peuvent provoquer la génération de noms que vous n'attendez pas.

Des prototypes de fonctions qui ont des paramètres non correspondants peuvent également provoquer cette erreur. La décoration de nom incorpore les paramètres d'une fonction dans le nom décoré final de la fonction. L'appel d'une fonction avec les types de paramètres qui ne correspondent pas à ceux de la déclaration de la fonction peut aussi causer l'erreur LNK2001.

Il n'existe actuellement aucune norme pour l'affectation de noms C++ entre les éditeurs de compilateurs ou même entre les différentes versions d'un compilateur. La liaison de fichiers objets compilés avec d'autres compilateurs peut donc ne pas produire le même schéma d'affectation de noms et aboutir ainsi à des noms externes non résolus.

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)