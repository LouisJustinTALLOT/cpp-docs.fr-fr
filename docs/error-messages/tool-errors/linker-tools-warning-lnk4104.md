---
title: Avertissement LNK4104 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4104
dev_langs:
- C++
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6304f3ea928c89f4756a4594270ebb7914324f85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057260"
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