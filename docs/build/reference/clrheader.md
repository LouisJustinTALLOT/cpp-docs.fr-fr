---
description: En savoir plus sur:/CLRHEADER
title: /CLRHEADER
ms.date: 05/16/2019
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 8866707ae629672c3ae9ebb468d145eafb0475c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182422"
---
# <a name="clrheader"></a>/CLRHEADER

Afficher les informations spécifiques au CLR.

## <a name="syntax"></a>Syntaxe

> *fichier* /CLRHEADER

### <a name="arguments"></a>Arguments

*file*<br/>
Fichier image généré avec [/clr](clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Notes

**/CLRHEADER** affiche des informations sur les en-têtes .NET utilisés dans n’importe quel programme managé. La sortie indique l’emplacement et la taille, en octets, de l’en-tête .NET et les sections dans l’en-tête.

Seule l’option [/HEADERS](headers.md) DUMPBIN peut être utilisée sur les fichiers générés avec l’option du compilateur [/GL](gl-whole-program-optimization.md).

Lorsque **/CLRHEADER** est utilisé sur un fichier qui a été compilé avec /clr, il y aura une section **clr Header:** dans la sortie DUMPBIN. La valeur de **flags** indique l’option /clr qui a été utilisée :

- 0  -- /clr (l’image peut contenir du code natif).

Vous pouvez également vérifier programmatiquement si une image a été générée pour le common language runtime.  Pour plus d’informations, consultez [Comment : déterminer si une image est native ou CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

Les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017 et ultérieur. Le code qui doit être « pur » ou « sécurisé » doit être porté sur C#.

## <a name="see-also"></a>Voir aussi

- [Options DUMPBIN](dumpbin-options.md)
