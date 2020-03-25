---
title: Avertissement des outils Éditeur de liens LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: aaa26393f1ce76d3e1bc40e5ba4978d1bcdb4fc9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193756"
---
# <a name="linker-tools-warning-lnk4237"></a>Avertissement des outils Éditeur de liens LNK4237

/SUBSYSTEM : NATIVE spécifié lors de l’importation à partir de’dll'; Utilisez/SUBSYSTEM : CONSOLE ou/SUBSYSTEM : WINDOWS.

[/SUBSYSTEM : Native](../../build/reference/subsystem-specify-subsystem.md) a été spécifié lors de la génération d’une application Windows (Win32) qui utilise directement un ou plusieurs des éléments suivants :

- kernel32.dll

- gdi32.dll

- user32.dll

- l’une des dll du\* Msvcrt.

Résolvez cet avertissement en ne spécifiant pas **/SUBSYSTEM : Native**.
