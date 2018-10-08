---
title: idl_quote (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_quote
dev_langs:
- C++
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f4050e78e6313b77808c1a1ed790e2b7082122d
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790593"
---
# <a name="idlquote"></a>idl_quote

Vous permet d’utiliser des constructions IDL qui ne sont pas pris en charge dans la version actuelle de Visual C++ et les passer au fichier .idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Paramètres

*texte*<br/>
Le nom d’attribut que vous avez l’intention le compilateur Visual C++ à passer au fichier .idl généré sans retourner une erreur du compilateur.

## <a name="remarks"></a>Notes

Si le **idl_quote** attribut C++ est utilisé comme un attribut autonome (avec un point-virgule après l’accolade fermante), puis *texte* est placé dans le fichier .idl fusionnée en l’état. Si **idl_quote** est utilisé sur un symbole, *texte* est placé dans le bloc d’attributs pour ce symbole.

## <a name="example"></a>Exemple

Le code suivant montre comment vous pouvez spécifier un attribut non pris en charge (à l’aide de **dans**, qui est pris en charge) et comment définir et utiliser une construction .idl non défini :

```cpp
// cpp_attr_ref_idl_quote.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];

[export]
struct MYFLOT {
   int i;
};

[export]
struct MYDUB {
   int i;
};

[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];

typedef struct _S1_TYPE {
   long l1;

union {
   MYFLOT f1; MYDUB d2; } U1_TYPE;
} S1_TYPE;

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]
__interface IStatic{
   HRESULT Func1([idl_quote("in")] int i);
   HRESULT func( S1_TYPE* myStruct );
};
```

Ce code provoque `MYFLOT` et `MYDUB` et *texte* entrée à placer dans le fichier .idl généré. Le *nom* paramètre force *texte* à être placé avant tout ce qui fait référence à *nom* dans le fichier .idl généré. Le *dépendances* paramètre force les définitions de liste de dépendance à être placé avant *texte* dans le fichier .idl généré.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)  