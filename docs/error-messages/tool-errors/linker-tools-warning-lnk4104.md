---
title: Avertissement des outils Éditeur de liens LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 604dccf01b3dffc0060546bebf19d64c16ebf965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193964"
---
# <a name="linker-tools-warning-lnk4104"></a>Avertissement des outils Éditeur de liens LNK4104

l’exportation du symbole’Symbol’doit être privée

La `symbol` peut être l’une des suivantes :

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

Cet avertissement est émis lorsque vous générez une bibliothèque d’importation pour une DLL et que vous exportez l’une des fonctions ci-dessus sans la spécifier comme privée dans le fichier de définition de module. En général, ces fonctions sont exportées uniquement pour une utilisation par OLE. Le fait de les placer dans la bibliothèque d’importation peut entraîner un comportement inhabituel lorsqu’un programme lié à la bibliothèque effectue incorrectement des appels à ces derniers. Pour plus d’informations sur le mot clé PRIVATE, consultez [exportations](../../build/reference/exports.md).
