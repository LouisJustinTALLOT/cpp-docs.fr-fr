---
title: Erreur du compilateur C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: da4c03c681f95efaa5edb159869315b41d027e99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303526"
---
# <a name="compiler-error-c2026"></a>Erreur du compilateur C2026

chaîne trop grande, caractères de fin tronqués

La chaîne était plus longue que la limite de 16380 caractères codés sur un octet.

Avant la concaténation des chaînes adjacentes, une chaîne ne peut pas dépasser 16380 caractères codés sur un octet.

Une chaîne Unicode d’environ la moitié de cette longueur générerait également cette erreur.

Si vous avez une chaîne définie comme suit, il génère C2026 :

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Vous pourriez la fractionner comme suit :

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Vous souhaiterez peut-être stocker les littéraux de chaîne de taille exceptionnelle (32 Ko ou plus) dans une ressource personnalisée ou d’un fichier externe. Consultez [création d’une ressource personnalisée ou ressource de données](../../windows/creating-a-new-custom-or-data-resource.md) pour plus d’informations.