---
title: idl_quote (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 4b05da6d237d71e0cc645ad0f626f75ecd85c827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168027"
---
# <a name="idl_quote"></a>idl_quote

Vous permet d’utiliser des constructions IDL qui ne sont pas prises en charge dans la version C++ actuelle de Visual et de les transmettre au fichier. idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Paramètres

*text*<br/>
Nom de l’attribut que vous souhaitez que C++ le compilateur Microsoft passe au fichier. idl généré sans retourner d’erreur du compilateur.

## <a name="remarks"></a>Notes

Si l’attribut **idl_quote** C++ est utilisé en tant qu’attribut autonome (avec un point-virgule après le crochet fermant), le *texte* est placé dans le fichier. idl fusionné tel quel. Si **idl_quote** est utilisé sur un symbole, le *texte* est placé dans le bloc d’attributs pour ce symbole.

## <a name="example"></a>Exemple

Le code suivant montre comment vous pouvez spécifier un attribut non pris en charge (à l’aide **de dans**, qui est pris en charge) et comment définir et utiliser une construction. idl non définie :

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

Ce code provoque l’insertion de `MYFLOT` et `MYDUB` et l’entrée de *texte* dans le fichier. idl généré. Le paramètre *Name* force le *texte* à être placé avant tout ce qui référence le *nom* dans le fichier. idl généré. Le paramètre *Dependencies* force les définitions de liste de dépendances à être placées avant le *texte* dans le fichier. idl généré.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)
