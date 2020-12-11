---
description: 'En savoir plus sur : décoration de nom'
title: Décoration de nom
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: 36360a1e313aba17a203fd1c2c4412cb927d1591
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155135"
---
# <a name="name-decoration"></a>Décoration de nom

La décoration de nom se rapporte généralement aux conventions d'affectation de noms C++, mais peut également s'appliquer à un certain nombre de cas du C. Par défaut, C++ utilise le nom de la fonction, les paramètres et le type de retour pour créer un nom d'éditeur de liens pour la fonction. Considérons la déclaration de fonction suivante :

`void CALLTYPE test(void);`

Le tableau suivant montre le nom de l'éditeur de liens pour différentes conventions d'appel.

|Convention d'appel|`extern "C"` ou `.c` fichier|`.cpp`, `.cxx` ou `/TP`|
|------------------------|---------------------------|------------------------|
|Convention d’affectation de noms C ( **`__cdecl`** )|`_test`|`?test@@ZAXXZ`|
|Convention d’affectation de noms des appels rapides ( **`__fastcall`** )|`@test@0`|`?test@@YIXXZ`|
|Convention de nommage des appels standard ( **`__stdcall`** )|`_test@0`|`?test@@YGXXZ`|
|Convention de nommage des appels de vecteurs ( **`__vectorcall`** )|`test@@0`|`?test@@YQXXZ`|

Utilisez `extern "C"` pour appeler une fonction C à partir de C++. `extern "C"` force l’utilisation de la Convention d’affectation de noms C pour les fonctions C++ sans classe. N’oubliez pas que le compilateur bascule **/TC** ou **/TP**, qui indique au compilateur d’ignorer l’extension de nom de fichier et de compiler le fichier en C ou C++, respectivement. Ces options peuvent entraîner des noms de l’éditeur de liens que vous n’attendez pas.

Des prototypes de fonctions qui ont des paramètres non correspondants peuvent également provoquer cette erreur. La décoration de nom incorpore les paramètres d'une fonction dans le nom décoré final de la fonction. L’appel d’une fonction avec les types de paramètres qui ne correspondent pas à ceux de la déclaration de fonction peut également causer LNK2001.

Il n’existe actuellement aucune norme pour le nommage C++ entre les fournisseurs de compilateurs ou même entre les différentes versions d’un compilateur. La liaison de fichiers objets compilés par d’autres compilateurs peut ne pas produire le même schéma d’affectation de noms et peut provoquer des externes non résolus.

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
