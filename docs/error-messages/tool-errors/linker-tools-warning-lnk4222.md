---
title: Avertissement des outils Éditeur de liens LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 52a4fee532eb9997dcf013f95246b27fdffc4c20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563096"
---
# <a name="linker-tools-warning-lnk4222"></a>Avertissement des outils Éditeur de liens LNK4222

un symbole exporté 'symbol' ne doit pas être assigné un ordinal

Les symboles suivants ne doivent pas être exportés par ordinal :

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Ces fonctions sont toujours situées par nom, à l’aide de `GetProcAddress`. L’éditeur de liens vous avertit à ce sujet est de type d’exportation, car cela peut entraîner une image plus grande. Cela peut se produire si la plage de vos exportations ordinales est grande avec relativement peu d’exportations. Par exemple :

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

nécessite 100 emplacements dans la table d’adresses exportation dont 98 remplisseur simplement (2-99). D'un autre côté

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

nécessite deux emplacements. (N’oubliez pas que vous pouvez également exporter avec la [/EXPORT](../../build/reference/export-exports-a-function.md) option de l’éditeur de liens.)