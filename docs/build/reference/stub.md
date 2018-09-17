---
title: STUB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151d7b425a7f397a05e3a06e9d94489a0c76f899
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725112"
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