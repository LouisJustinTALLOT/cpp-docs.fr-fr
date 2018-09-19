---
title: Avertissement LNK4205 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4205
dev_langs:
- C++
helpviewer_keywords:
- LNK4205
ms.assetid: d63b9d18-ef3c-4081-9d8d-93077dad13c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e76cef24436fc5ce3468a1c94be2d1a49733525a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105529"
---
# <a name="linker-tools-warning-lnk4205"></a>Avertissement des outils Éditeur de liens LNK4205

Il manque des informations de débogage en cours pour référencer le module ; 'nom_fichier' objet sera lié sans informations de débogage

Le fichier .pdb a des informations obsolètes. L’éditeur de liens poursuit la liaison d’objet sans informations de débogage. Vous souhaiterez peut-être recompiler le fichier objet en utilisant le [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) option.