---
title: Décoration de nom
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: cc00c971eac2a089ccec5bd9eab594bdf4e8348e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173515"
---
# <a name="name-decoration"></a>Décoration de nom

La décoration de nom se rapporte généralement aux conventions d'affectation de noms C++, mais peut également s'appliquer à un certain nombre de cas du C. Par défaut, C++ utilise le nom de la fonction, les paramètres et le type de retour pour créer un nom d'éditeur de liens pour la fonction. Considérons la déclaration de fonction suivante :

`void CALLTYPE test(void);`

Le tableau suivant montre le nom de l'éditeur de liens pour différentes conventions d'appel.

|Convention d'appel|fichier `extern "C"` ou `.c`|`.cpp`, `.cxx` ou `/TP`|
|------------------------|---------------------------|------------------------|
|Convention d'affectation de noms C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Convention de nommage des appels rapides (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Convention de nommage des appels standard (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Convention de nommage des appels de vecteurs (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Utilisez `extern "C"` pour appeler une fonction C à C++partir de. `extern "C"` force l’utilisation de la Convention d’affectation de noms C C++ pour les fonctions qui ne sont pas de classe. N’oubliez pas que le compilateur bascule **/TC** ou **/TP**, qui indique au compilateur d’ignorer l’extension de nom de fichier et de C++compiler le fichier en tant que C ou, respectivement. Ces options peuvent entraîner des noms de l’éditeur de liens que vous n’attendez pas.

Des prototypes de fonctions qui ont des paramètres non correspondants peuvent également provoquer cette erreur. La décoration de nom incorpore les paramètres d'une fonction dans le nom décoré final de la fonction. L’appel d’une fonction avec les types de paramètres qui ne correspondent pas à ceux de la déclaration de fonction peut également causer LNK2001.

Il n’existe actuellement aucune norme C++ pour nommer les fournisseurs de compilateur, ni même entre les différentes versions d’un compilateur. La liaison de fichiers objets compilés par d’autres compilateurs peut ne pas produire le même schéma d’affectation de noms et peut provoquer des externes non résolus.

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
