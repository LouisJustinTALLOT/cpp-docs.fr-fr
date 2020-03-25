---
title: Erreur du compilateur C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 9747b1edadc76ceeb502b2c6fd03496b91769f5a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208063"
---
# <a name="compiler-error-c2026"></a>Erreur du compilateur C2026

chaîne trop grande, caractères de fin tronqués

La chaîne dépasse la limite de 16380 caractères sur un octet.

Avant les chaînes adjacentes concaténées, une chaîne ne peut pas dépasser 16380 caractères codés sur un octet.

Une chaîne Unicode d’environ une moitié de cette longueur générerait également cette erreur.

Si une chaîne est définie comme suit, elle génère C2026 :

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Vous pouvez le décomposer comme suit :

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Vous souhaiterez peut-être stocker des littéraux de chaîne exceptionnellement volumineux (32 Ko ou plus) dans une ressource personnalisée ou un fichier externe. Pour plus d’informations, consultez [création d’une ressource de données ou personnalisée](../../windows/creating-a-new-custom-or-data-resource.md) .
