---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: fd2e7c4a3bd9fa09b88f4c3caa9b7d5b73c1ad98
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412937"
---
# <a name="stub"></a>STUB

Lorsqu’il est utilisé dans un fichier de définition de module qui génère un pilote de périphérique virtuel (VxD), vous permet de spécifier un nom de fichier qui contient une structure IMAGE_DOS_HEADER (définie dans WINNT. (H) à utiliser dans le pilote de périphérique virtuel (VxD), au lieu de l’en-tête par défaut.

```
STUB:filename
```

## <a name="remarks"></a>Notes

Vous pouvez spécifier *filename* consiste à utiliser le [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) option de l’éditeur de liens.

STUB est valide dans un fichier de définition de module uniquement lors de la création d’un VxD.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)
