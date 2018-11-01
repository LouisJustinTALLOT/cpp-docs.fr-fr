---
title: DHtmlUrlEventMapEntry, structure
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: 0a1dc86080c094a7ac89940cd43a8edac973e10c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431627"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry, structure

Le `DHtmlUrlEventMapEntry` structure fournit la prise en charge des cartes avec plusieurs URL événement.

## <a name="syntax"></a>Syntaxe

```
struct DHtmlUrlEventMapEntry
{
LPCTSTR szUrl;
const DHtmlEventMapEntry *pEventMap;
};
```

#### <a name="parameters"></a>Paramètres

*szUrl*<br/>
L’URL.

*pEventMap*<br/>
La table d’événements associée à l’URL.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdhtml.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

