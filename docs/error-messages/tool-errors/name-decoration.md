---
title: Décoration de nom
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857167"
---
# <a name="name-decoration"></a>Décoration de nom

La décoration de nom se rapporte généralement aux conventions d'affectation de noms C++, mais peut également s'appliquer à un certain nombre de cas du C. Par défaut, C++ utilise le nom de la fonction, les paramètres et le type de retour pour créer un nom d'éditeur de liens pour la fonction. Considérons la déclaration de fonction suivante :

`void CALLTYPE test(void);`

Le tableau suivant montre le nom de l'éditeur de liens pour différentes conventions d'appel.

|Convention d'appel|`extern "C"` ou `.c` fichier|`.cpp`, `.cxx` ou `/TP`|
|------------------------|---------------------------|------------------------|
|Convention d'affectation de noms C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Convention d’affectation de noms appel rapide (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standard appeler convention d’affectation de noms (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Vector, convention d’affectation de noms appel (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Utilisez `extern "C"` pour appeler une fonction C à partir de C++. `extern "C"` force l’utilisation de la convention d’affectation de noms C pour sans classe C++ fonctions. N’oubliez pas de commutateurs du compilateur **TP** ou **/Tp**, qui indiquent au compilateur d’ignorer l’extension de nom de fichier et de compiler le fichier en tant que C ou C++, respectivement. Ces options peuvent causer des noms de l’éditeur de liens que vous ne pensez pas.

Des prototypes de fonctions qui ont des paramètres non correspondants peuvent également provoquer cette erreur. La décoration de nom incorpore les paramètres d'une fonction dans le nom décoré final de la fonction. Appel d’une fonction avec les types de paramètres qui ne correspondent à celles figurant dans la déclaration de fonction peut aussi causer LNK2001.

Il n’existe actuellement aucune norme C++ d’affectation de noms entre les éditeurs de compilateurs ou même entre différentes versions d’un compilateur. Liaison de fichiers objets compilés par d’autres compilateurs peut ne pas produire le même schéma d’affectation de noms et peut provoquer des externes non résolus.

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)