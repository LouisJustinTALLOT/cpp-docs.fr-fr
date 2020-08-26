---
title: RDX (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f61eaf535102c8885e828176434acf221dfe2457
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836879"
---
# <a name="rdx"></a>rdx

Crée une clé de registre ou modifie une clé de Registre existante.

## <a name="syntax"></a>Syntaxe

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Nom de la clé à créer ou ouvrir.

*valueName*<br/>
Facultatif Spécifie le champ de valeur à définir. Si un champ de valeur portant ce nom n’existe pas déjà dans la clé, il est ajouté.

*regtype*<br/>
Type de clé de Registre ajoutée. Il peut s’agir de l’une des valeurs suivantes : `text` ,, `dword` `binary` ou `CString` .

## <a name="remarks"></a>Notes

L’attribut C++ **RDX** crée ou modifie une clé de Registre existante pour un composant com. L’attribut ajoute une macro BEGIN_RDX_MAP à l’objet qui implémente le membre cible. `RegistryDataExchange`, une fonction injectée à la suite de la macro BEGIN_RDX_MAP, peut être utilisée pour transférer des données entre le registre et les membres de données.

Cet attribut peut être utilisé conjointement avec les attributs [coclass](coclass.md), [ProgID](progid.md)ou [vi_progid](vi-progid.md) ou d’autres attributs qui impliquent l’un de ces attributs.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`****`struct`** membre ou|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Exemple

Le code suivant ajoute une clé de Registre nommée MyValue au système décrivant le composant de modèle d’élément de configuration (CMyClass).

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[registration_script](registration-script.md)
