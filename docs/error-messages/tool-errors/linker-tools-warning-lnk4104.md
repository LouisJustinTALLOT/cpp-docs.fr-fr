---
title: Avertissement des outils Éditeur de liens LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 3d89b27c32b33b917abb7fc140eebf5924142423
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298540"
---
# <a name="linker-tools-warning-lnk4104"></a>Avertissement des outils Éditeur de liens LNK4104

exportation du symbole 'symbole' doit être PRIVATE

Le `symbol` peut prendre l’une des opérations suivantes :

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

Cet avertissement est émis lorsque vous générez une bibliothèque d’importation pour une DLL et exporter une des fonctions ci-dessus sans spécifier comme privés dans le fichier de définition de module. En règle générale, ces fonctions sont exportées pour une utilisation uniquement par OLE. En les plaçant dans la bibliothèque d’importation peuvent entraîner un comportement inhabituel lorsqu’un programme lié à la bibliothèque de manière incorrecte effectue des appels pour eux. Pour plus d’informations sur le mot clé privé, consultez [exportations](../../build/reference/exports.md).