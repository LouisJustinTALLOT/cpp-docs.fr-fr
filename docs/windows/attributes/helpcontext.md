---
title: HelpContext (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 22023b4087c67b62d540d021fa06fd3582c7e4e2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038158"
---
# <a name="helpcontext"></a>helpcontext

Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le **aide** fichier.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
ID de contexte de la rubrique d’aide. Consultez [aide HTML : Aide contextuelle pour vos programmes](../../mfc/html-help-context-sensitive-help-for-your-programs.md) pour plus d’informations sur l’ID de contexte.

## <a name="remarks"></a>Notes

Le **helpcontext** attribut C++ a les mêmes fonctionnalités que le [helpcontext](/windows/desktop/Midl/helpcontext) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [defaultvalue](defaultvalue.md) pour obtenir un exemple montrant comment utiliser **helpcontext**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **typedef**, **class**, method, property|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)