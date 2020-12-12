---
description: 'En savoir plus sur : structure Dhtmlurleventmapentry,'
title: DHtmlUrlEventMapEntry, structure
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: c35e3ac70d8530042ca73397b0f7c6df13501497
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220056"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry, structure

La `DHtmlUrlEventMapEntry` structure fournit la prise en charge de la carte d’événements à plusieurs URL.

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
URL.

*pEventMap*<br/>
Table d’événements associée à l’URL.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdhtml. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
