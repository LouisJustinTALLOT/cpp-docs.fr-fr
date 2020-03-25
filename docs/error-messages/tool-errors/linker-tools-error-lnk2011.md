---
title: Erreur des outils Éditeur de liens LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: e08f068099af68375523eae0f0cc4d63960f3261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194809"
---
# <a name="linker-tools-error-lnk2011"></a>Erreur des outils Éditeur de liens LNK2011

objet précompilé non lié dans ; l’image risque de ne pas s’exécuter

Si vous utilisez des en-têtes précompilés, LINK exige que tous les fichiers objets créés avec des en-têtes précompilés soient liés. Si vous avez un fichier source que vous utilisez pour générer un en-tête précompilé à utiliser avec d’autres fichiers sources, vous devez maintenant inclure le fichier objet créé avec l’en-tête précompilé.

Par exemple, si vous compilez un fichier appelé STUB. cpp pour créer un en-tête précompilé à utiliser avec d’autres fichiers sources, vous devez effectuer une liaison avec STUB. obj. sinon, vous obtiendrez cette erreur. Dans les lignes de commande suivantes, la ligne 1 est utilisée pour créer un en-tête précompilé, COMMON. pch, qui est utilisé avec PROG1. cpp et PROG2. cpp dans les lignes deux et trois. Le fichier STUB. cpp contient uniquement des lignes `#include` (les mêmes lignes de `#include` que dans PROG1. cpp et PROG2. cpp) et est utilisé uniquement pour générer des en-têtes précompilés. Dans la dernière ligne, STUB. obj doit être lié pour éviter LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
