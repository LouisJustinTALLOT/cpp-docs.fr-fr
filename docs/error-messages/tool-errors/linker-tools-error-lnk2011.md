---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2011'
title: Erreur des outils Éditeur de liens LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: f149324a61d34333e8f29f70bf5fee4cd952ba8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338474"
---
# <a name="linker-tools-error-lnk2011"></a>Erreur des outils Éditeur de liens LNK2011

objet précompilé non lié dans ; l’image risque de ne pas s’exécuter

Si vous utilisez des en-têtes précompilés, LINK exige que tous les fichiers objets créés avec des en-têtes précompilés soient liés. Si vous avez un fichier source que vous utilisez pour générer un en-tête précompilé à utiliser avec d’autres fichiers sources, vous devez maintenant inclure le fichier objet créé avec l’en-tête précompilé.

Par exemple, si vous compilez un fichier appelé STUB. cpp pour créer un en-tête précompilé à utiliser avec d’autres fichiers sources, vous devez effectuer une liaison avec STUB. obj. sinon, vous obtiendrez cette erreur. Dans les lignes de commande suivantes, la ligne 1 est utilisée pour créer un en-tête précompilé, COMMON. pch, qui est utilisé avec PROG1. cpp et PROG2. cpp dans les lignes deux et trois. Le fichier STUB. cpp contient uniquement des `#include` lignes (les mêmes `#include` lignes que dans PROG1. cpp et PROG2. cpp) et est utilisé uniquement pour générer des en-têtes précompilés. Dans la dernière ligne, STUB. obj doit être lié pour éviter LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
