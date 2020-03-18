---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4f5b662223914cbb4970188595afb52cc2500cd4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440390"
---
# <a name="allowbind"></a>/ALLOWBIND

Spécifie si une DLL peut être liée.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Notes

L’option **/ALLOWBIND** définit un bit dans l’en-tête d’une dll qui indique à bind. exe que l’image est autorisée à être liée. La liaison peut permettre à une image de se charger plus rapidement lorsque le chargeur n’a pas besoin de rebaser et d’effectuer la correction d’adresse pour chaque DLL référencée. Vous ne souhaiterez peut-être pas qu’une DLL soit liée si elle a été signée numériquement ; la liaison invalide la signature. La liaison n’a aucun effet si la randomisation du format d’espace d’adresse (ASLR) est activée pour l’image à l’aide de **/DynamicBase** sur les versions de Windows qui prennent en charge ASLR.

Utilisez **/ALLOWBIND : no** pour empêcher bind. exe de lier la dll.

Pour plus d’informations, consultez l’option de l’éditeur de liens [/ALLOWBIND](allowbind-prevent-dll-binding.md) .

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
