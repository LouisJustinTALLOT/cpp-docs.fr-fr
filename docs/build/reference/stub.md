---
description: 'En savoir plus sur : STUB'
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 79a2002c119bf211652e2aab51d9656b36e3d159
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230287"
---
# <a name="stub"></a>STUB

Lorsqu’il est utilisé dans un fichier de définition de module qui crée un pilote de périphérique virtuel (VxD), vous permet de spécifier un nom de fichier qui contient une structure de IMAGE_DOS_HEADER (définie dans WINNt. H) à utiliser dans le pilote de périphérique virtuel (VxD), plutôt que dans l’en-tête par défaut.

```
STUB:filename
```

## <a name="remarks"></a>Notes

L’option [/stub](stub-ms-dos-stub-file-name.md) de l’éditeur de liens permet de spécifier un *nom de fichier* équivalent.

Le STUB est valide dans un fichier de définition de module uniquement lors de la génération d’un VxD.

## <a name="see-also"></a>Voir aussi

[Règles pour les instructions Module-Definition](rules-for-module-definition-statements.md)
