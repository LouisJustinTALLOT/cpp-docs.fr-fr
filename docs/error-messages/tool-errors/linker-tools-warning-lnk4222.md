---
title: LNK4222 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359af4c4d3b1079b2d56f108bff0ee1488ea71f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302147"
---
# <a name="linker-tools-warning-lnk4222"></a>Avertissement des outils Éditeur de liens LNK4222
un symbole exporté 'symbole' ne doit pas être attribué un ordinal  
  
 Les symboles suivants ne doivent pas être exportés par ordinal :  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 Ces fonctions sont toujours situées par nom, à l’aide de `GetProcAddress`. L’éditeur de liens vous avertit sur ce type d’exportation est, car elle peut entraîner une image plus grande. Cela peut se produire si la plage de vos exportations ordinales est grande avec relativement peu d’exportations. Par exemple :  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 nécessite 100 emplacements dans la table d’adresses exportation dont 98 remplisseur simplement de (2-99). D'un autre côté  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 nécessite deux emplacements. (Sachez que vous pouvez également exporter avec la [/EXPORT](../../build/reference/export-exports-a-function.md) option de l’éditeur de liens.)