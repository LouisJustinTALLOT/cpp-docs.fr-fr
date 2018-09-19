---
title: LNK2011 d’erreur des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2011
dev_langs:
- C++
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18562a21886508ff0766641f95ac2e15b76fd424
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095389"
---
# <a name="linker-tools-error-lnk2011"></a>Erreur des outils Éditeur de liens LNK2011

objet précompilé ne pas de liens ; image ne peut pas s’exécuter

Si vous utilisez des en-têtes précompilés, LINK requiert que tous les fichiers objets créés avec des en-têtes précompilés soient liés. Si vous avez un fichier source que vous utilisez pour générer un en-tête précompilé pour une utilisation avec d’autres fichiers de code source, vous devez maintenant inclure le fichier objet créé avec l’en-tête précompilé.

Par exemple, si vous compilez un fichier appelé STUB.cpp pour créer un en-tête précompilé pour une utilisation avec d’autres fichiers de code source, vous devez le lier avec stub.obj sous ou vous obtiendrez cette erreur. Dans les lignes de commande suivantes, ligne une est utilisée pour créer un en-tête précompilé, COMMON.pch, utilisé avec PROG1.cpp et PROG2.cpp dans les lignes deux et trois. Le fichier stub.cpp ne contient que `#include` lignes (le même `#include` lignes, comme dans PROG1.cpp et PROG2.cpp) et est utilisé uniquement pour générer des en-têtes précompilés. Dans la dernière ligne, stub.obj sous doit liée afin d’éviter LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```