---
title: -CLRHEADER | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cda2f03e8a0473d2c45f54c96ca97b043d80d5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704439"
---
# <a name="clrheader"></a>/CLRHEADER

Afficher les informations spécifiques au CLR.

## <a name="syntax"></a>Syntaxe

> / /CLRHEADER *fichier*

### <a name="arguments"></a>Arguments

|||
|-|-|
*fichier*| Génération d’un fichier image avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Notes

**/ /CLRHEADER** affiche des informations sur les en-têtes .NET utilisés dans un programme managé. La sortie indique l’emplacement et la taille, en octets, de l’en-tête .NET et les sections dans l’en-tête.

Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés par le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.

Lorsque **/CLRHEADER** est utilisé sur un fichier qui a été compilé avec/CLR, il y aura un **clr Header :** section dans la sortie de dumpbin. La valeur de **indicateurs** indique l’option /clr qui a été utilisée :

- 0--/clr (image peut contenir du code natif).

Vous pouvez également vérifier par programme si une image a été créée pour le common language runtime.  Pour plus d’informations, consultez [Comment : déterminer si une Image est Native ou CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Le code qui doit être « pure » ou « sécurisée » doit être déplacée vers c#.

## <a name="see-also"></a>Voir aussi

- [DUMPBIN, options](../../build/reference/dumpbin-options.md)
