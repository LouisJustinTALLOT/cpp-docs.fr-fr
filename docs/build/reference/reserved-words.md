---
description: 'En savoir plus sur : mots réservés'
title: Mots réservés
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 6d5c5971d8d01dffa1dcd1e7f6a5228fb239d4dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225191"
---
# <a name="reserved-words"></a>Mots réservés

Les mots suivants sont réservés par l’éditeur de liens. Ces noms peuvent être utilisés comme arguments dans les [instructions de définition de module](module-definition-dot-def-files.md) uniquement si le nom est placé entre guillemets doubles ("").

:::row:::
   :::column span="":::
      **`APPLOADER`**<sup>1,0</sup>\
      **`BASE`**\
      **`CODE`**\
      **`CONFORMING`**\
      **`DATA`**\
      **`DESCRIPTION`**\
      **`DEV386`**\
      **`DISCARDABLE`**\
      **`DYNAMIC`**\
      **`EXECUTE-ONLY`**\
      **`EXECUTEONLY`**\
      **`EXECUTEREAD`**\
      **`EXETYPE`**\
      **`EXPORTS`**\
      **`FIXED`**<sup>1,0</sup>
   :::column-end:::
   :::column span="":::
      **`FUNCTIONS`**<sup>2</sup>\
      **`HEAPSIZE`**\
      **`IMPORTS`**\
      **`IMPURE`**<sup>1,0</sup>\
      **`INCLUDE`**<sup>2</sup>\
      **`INITINSTANCE`**<sup>2</sup>\
      **`IOPL`**\
      **`LIBRARY`**<sup>1,0</sup>\
      **`LOADONCALL`**<sup>1,0</sup>\
      **`LONGNAMES`**<sup>2</sup>\
      **`MOVABLE`**<sup>1,0</sup>\
      **`MOVEABLE`**<sup>1,0</sup>\
      **`MULTIPLE`**\
      **`NAME`**\
      **`NEWFILES`**<sup>2</sup>
   :::column-end:::
   :::column span="":::
      **`NODATA`**<sup>1,0</sup>\
      **`NOIOPL`**<sup>1,0</sup>\
      **`NONAME`**\
      **`NONCONFORMING`**<sup>1,0</sup>\
      **`NONDISCARDABLE`**\
      **`NONE`**\
      **`NONSHARED`**\
      **`NOTWINDOWCOMPAT`**<sup>1,0</sup>\
      **`OBJECTS`**\
      **`OLD`**<sup>1,0</sup>\
      **`PRELOAD`**\
      **`PRIVATE`**\
      **`PROTMODE`**<sup>2</sup>\
      **`PURE`**<sup>1,0</sup>\
      **`READONLY`**
   :::column-end:::
   :::column span="":::
      **`READWRITE`**\
      **`REALMODE`**<sup>1,0</sup>\
      **`RESIDENT`**\
      **`RESIDENTNAME`**<sup>1,0</sup>\
      **`SECTIONS`**\
      **`SEGMENTS`**\
      **`SHARED`**\
      **`SINGLE`**\
      **`STACKSIZE`**\
      **`STUB`**\
      **`VERSION`**\
      **`WINDOWAPI`**\
      **`WINDOWCOMPAT`**\
      **`WINDOWS`**
   :::column-end:::
:::row-end:::

<sup>1</sup> l’éditeur de liens émet un avertissement (« ignoré ») lorsqu’il rencontre ce terme. Toutefois, le mot est toujours réservé.

<sup>2</sup> l’éditeur de liens ignore ce mot mais n’émet aucun avertissement.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
