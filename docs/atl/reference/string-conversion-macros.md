---
title: Macros de Conversion de chaîne | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 917afc7dae7a0ed96d5d5cc476b4f8394abe8913
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362973"
---
# <a name="string-conversion-macros"></a>Macros de Conversion de chaînes

Ces macros fournissent des fonctionnalités de conversion de chaîne.  
 
##  <a name="atl_and_mfc_string_conversion_macros"></a>  Macros de Conversion de chaînes MFC et ATL

Les macros de conversion de chaînes présentées ici sont valides à la fois pour ATL et pour MFC. Pour plus d’informations sur la conversion de chaînes MFC, consultez [TN059 : à l’aide de Macros de Conversion MBCS/Unicode MFC](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) et [MFC Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  DEVMODE et Macros de Conversion de chaînes TEXTMETRIC

Ces macros créent une copie d’un [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) ou [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) structurer et convertir les chaînes dans la nouvelle structure en un nouveau type de chaîne. Les macros allocation de mémoire sur la pile pour la nouvelle structure et retournent un pointeur vers la nouvelle structure.  
  
```cpp
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>Notes

Par exemple :  
  
[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
et  
  
[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
Les noms de macro, le type de chaîne dans la structure source se trouve sur la gauche (par exemple, **A**) et le type de chaîne dans la structure de destination se trouve à droite (par exemple, **W**). **A** signifie `LPSTR`, **OLE** signifie `LPOLESTR`, **T** signifie `LPTSTR`, et **W** signifie `LPWSTR`.  
  
Par conséquent, **DEVMODEA2W** copies un `DEVMODE` structure avec `LPSTR` des chaînes dans un `DEVMODE` structure avec `LPWSTR` chaînes, **TEXTMETRICOLE2T** copie un `TEXTMETRIC`structure avec `LPOLESTR` des chaînes dans un `TEXTMETRIC` avec la structure `LPTSTR` chaînes et ainsi de suite.  
  
Les deux chaînes converties dans le `DEVMODE` structure sont le nom du périphérique (`dmDeviceName`) et le nom du formulaire (`dmFormName`). Le `DEVMODE` macros de conversion de chaînes également mettre à jour de la taille de la structure (`dmSize`).  
  
Les quatre chaînes converties dans le `TEXTMETRIC` structure sont le premier caractère (`tmFirstChar`), le dernier caractère (`tmLastChar`), le caractère par défaut (`tmDefaultChar`) et le caractère de saut (`tmBreakChar`).
  
Le comportement de la `DEVMODE` et `TEXTMETRIC` macros de conversion de chaînes dépend de la directive de compilateur en vigueur, le cas échéant. Si les types source et de destination sont les mêmes, aucune conversion n'est effectuée. Modifier les directives de compilateur **T** et **OLE** comme suit :  
  
|Directive du compilateur appliquée|T devient|OLE devient|  
|----------------------------------|---------------|-----------------|  
|aucun|**A**|**W**|  
|**\_UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**\_UNICODE** et **OLE2ANSI**|**W**|**A**|  
  
 Le tableau suivant répertorie les `DEVMODE` et `TEXTMETRIC` macros de conversion de chaîne.  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
