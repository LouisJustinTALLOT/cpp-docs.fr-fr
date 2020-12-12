---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4237'
title: Avertissement des outils Éditeur de liens LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: 9f8af2d6f0fa2d1153af749e327e95b863ed6914
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259992"
---
# <a name="linker-tools-warning-lnk4237"></a>Avertissement des outils Éditeur de liens LNK4237

/SUBSYSTEM : NATIVE spécifié lors de l’importation à partir de’dll'; Utilisez/SUBSYSTEM : CONSOLE ou/SUBSYSTEM : WINDOWS.

[/SUBSYSTEM : Native](../../build/reference/subsystem-specify-subsystem.md) a été spécifié lors de la génération d’une application Windows (Win32) qui utilise directement un ou plusieurs des éléments suivants :

- kernel32.dll

- gdi32.dll

- user32.dll

- une des DLL msvcrt \* .

Résolvez cet avertissement en ne spécifiant pas **/SUBSYSTEM : Native**.
