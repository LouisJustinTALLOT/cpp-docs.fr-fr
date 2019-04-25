---
title: DHtmlUrlEventMapEntry, structure
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: c9b58067a9c8b6a71cd22b654a2f82ba0f8bfe36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322733"
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
