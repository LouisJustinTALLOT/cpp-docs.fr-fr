---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4104'
title: Avertissement des outils Éditeur de liens LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: ab48885a4a8d2806154d3a8911bdc65453359e2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294429"
---
# <a name="linker-tools-warning-lnk4104"></a>Avertissement des outils Éditeur de liens LNK4104

l’exportation du symbole’Symbol’doit être privée

`symbol`Peut prendre l’une des valeurs suivantes :

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
