---
title: -ALLOWBIND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce0a33ebb0b8b9ba34ac241c8335e9524dec08b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715570"
---
# <a name="allowbind"></a>/ALLOWBIND

Spécifie si une DLL peut être liée.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Notes

Le **/ALLOWBIND** option définit un bit dans l’en-tête d’une DLL qui indique à Bind.exe que l’image est autorisée à être liée. Liaison permettre autoriser une image à charger plus rapidement lorsque le chargeur n’a pas à relocaliser et effectuer la correction de l’adresse pour chaque DLL référencée. Vous ne souhaiterez pas une DLL soit liée si elle a été signé numériquement, la liaison invalide la signature. Liaison n’a aucun effet si la randomisation du format d’espace d’adresse (ASLR) est activée pour l’image à l’aide de **/DYNAMICBASE** sur les versions de Windows qui prennent en charge ASLR.

Utilisez **/ALLOWBIND : no** pour empêcher la liaison de la DLL Bind.exe.

Pour plus d’informations, consultez le [/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) option de l’éditeur de liens.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](../../build/reference/editbin-options.md)