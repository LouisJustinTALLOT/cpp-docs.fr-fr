---
title: Erreur du compilateur C2026
description: Décrit les erreurs du compilateur Microsoft C/C++ C2026, ses causes et comment les résoudre.
ms.date: 09/25/2020
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 39195568f964f07c6131fa43ef4a0f06121795da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414046"
---
# <a name="compiler-error-c2026"></a>Erreur du compilateur C2026

> chaîne trop grande, caractères de fin tronqués

La chaîne dépasse la limite de 16380 caractères sur un octet.

## <a name="remarks"></a>Notes

Avant que les chaînes adjacentes soient concaténées, une chaîne ne peut pas dépasser 16380 caractères codés sur un octet.

Une chaîne Unicode d’environ une moitié de cette longueur générerait également cette erreur.

## <a name="example"></a>Exemple

Si une chaîne est définie comme suit, elle génère C2026 :

```C
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Vous pouvez le décomposer comme suit :

```C
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Vous souhaiterez peut-être stocker des littéraux de chaîne exceptionnellement volumineux (32 Ko ou plus) dans une ressource personnalisée ou un fichier externe. Pour plus d’informations, consultez [pour créer une ressource personnalisée ou une ressource de données](../../windows/binary-editor.md#to-create-a-new-custom-or-data-resource).
