---
title: Macro de conversion de cordes
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: 8df496b78334d26e7d3664642b2e9d93d6149843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325851"
---
# <a name="string-conversion-macros"></a>Macro de conversion de cordes

Ces macros fournissent des caractéristiques de conversion des chaînes.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>Macro de conversion des cordes ATL et MFC

Les macros de conversion de chaînes présentées ici sont valides à la fois pour ATL et pour MFC. Pour plus d’informations sur la conversion des chaînes MFC, voir [TN059: Using MFC MBCS/Unicode Conversion Macros](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) and [MFC Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>DeVMODE et TEXTMETRIC String Conversion Macros

Ces macros créent une copie d’une structure [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) ou [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) et convertissent les cordes de la nouvelle structure en un nouveau type de chaîne. Les macros allouent la mémoire sur la pile pour la nouvelle structure et retournent un pointeur à la nouvelle structure.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Notes

Par exemple :

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

et

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

Dans les noms macro, le type de chaîne dans la structure source est sur la gauche (par exemple, **A**) et le type de chaîne dans la structure de destination est sur la droite (par exemple, **W**). **Un** peuplement pour LPSTR, **OLE** signifie LPOLESTR, **T** signifie LPTSTR, et **W** signifie LPWSTR.

Ainsi, DEVMODEA2W `DEVMODE` copie une structure avec des `DEVMODE` cordes LPSTR dans une structure avec des `TEXTMETRIC` cordes LPWSTR, `TEXTMETRIC` TEXTMETRICOLE2T copie une structure avec des cordes LPOLESTR dans une structure avec des cordes LPTSTR, et ainsi de suite.

Les deux chaînes converties `DEVMODE` dans la structure`dmDeviceName`sont le nom`dmFormName`de l’appareil ( ) et le nom de forme ( ). Les `DEVMODE` macros de conversion de`dmSize`chaîne mettent également à jour la taille de la structure ().

Les quatre cordes converties `TEXTMETRIC` dans la structure`tmFirstChar`sont le`tmLastChar`premier personnage (), le dernier personnage (), le caractère par défaut (`tmDefaultChar`), et le caractère de rupture (`tmBreakChar`).

Le comportement `DEVMODE` des `TEXTMETRIC` macros de conversion et de chaîne dépend de la directive compilateur en vigueur, le cas échéant. Si les types source et de destination sont les mêmes, aucune conversion n'est effectuée. Les directives compilateur changent **T** et **OLE** comme suit :

|Directive du compilateur appliquée|T devient|OLE devient|
|----------------------------------|---------------|-----------------|
|Aucun|**A**|**W**|
|**\_Unicode**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE et **OLE2ANSI** ** \_**|**W**|**A**|

Le tableau suivant `DEVMODE` `TEXTMETRIC` répertorie les macros de conversion et les chaînes.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W TEXTMETRICAW TEXTMETRICAW TEXTMETRICAW|
|DEVMODEOLE2T|TEXTMETRICOLE2T TEXTMETRICOLE2T TEXTMETRICOLE|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A TEXTMETRICW2A|

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
