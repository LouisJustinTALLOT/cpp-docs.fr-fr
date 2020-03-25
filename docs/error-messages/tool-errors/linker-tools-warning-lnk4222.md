---
title: Avertissement des outils Éditeur de liens LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: f74379861ad04142fd78a8e307af165072c9cadd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183031"
---
# <a name="linker-tools-warning-lnk4222"></a>Avertissement des outils Éditeur de liens LNK4222

un symbole exporté’Symbol’ne doit pas être assigné à un ordinal

Les symboles suivants ne doivent pas être exportés par ordinal :

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Ces fonctions sont toujours situées par nom, à l’aide de `GetProcAddress`. L’éditeur de liens avertit ce type d’exportation, car cela peut entraîner une image plus grande. Cela peut se produire si la plage de vos exportations ordinales est importante avec relativement peu d’exportations. Par exemple,

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

nécessite 100 emplacements dans la table d’adresses d’exportation avec 98 (2-99) le remplissage. D'un autre côté

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

nécessite deux emplacements. (Sachez que vous pouvez également exporter avec l’option de l’éditeur de liens [/Export](../../build/reference/export-exports-a-function.md) .)
