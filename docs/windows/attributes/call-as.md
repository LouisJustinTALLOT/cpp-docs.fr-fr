---
description: 'En savoir plus sur : call_as'
title: call_as (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: de407da1401479327185c6133c625d61e1e221cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247447"
---
# <a name="call_as"></a>call_as

Permet à une fonction [locale](local-cpp.md) d’être mappée à une fonction distante afin que, lorsque la fonction distante est appelée, la fonction locale soit appelée.

## <a name="syntax"></a>Syntaxe

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Paramètres

*function*<br/>
Fonction locale que vous souhaitez appeler lorsqu’une fonction distante est appelée.

## <a name="remarks"></a>Notes

L’attribut C++ **call_as** a les mêmes fonctionnalités que l’attribut MIDL [call_as](/windows/win32/Midl/call-as) .

## <a name="example"></a>Exemple

Le code suivant montre comment vous pouvez utiliser **call_as** pour mapper une fonction qui n’est pas accessible à distance ( `f1` ) à une fonction accessible à distance ( `Remf1` ) :

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[localisé](local-cpp.md)
