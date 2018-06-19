---
title: idl_quote | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: a8844a4770d0a4746c9d9de32a593d0770dcc9a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878510"
---
# <a name="idlquote"></a>idl_quote
Vous pouvez utiliser des constructions IDL qui ne sont pas pris en charge dans la version actuelle de Visual C++ et les transmettre au fichier .idl généré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ idl_quote(  
   text  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *texte*  
 Le nom d’attribut que vous avez l’intention le compilateur Visual C++ pour passer directement vers le fichier .idl généré sans retourner une erreur du compilateur.  
  
## <a name="remarks"></a>Notes  
 Si le **idl_quote** attribut C++ est utilisé en tant qu’attribut autonome (avec un point-virgule après le crochet fermant), puis *texte* est placé dans le fichier .idl fusionné. Si **idl_quote** est utilisé sur un symbole, *texte* est placé dans le bloc d’attributs de ce symbole.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment vous pouvez spécifier un attribut non pris en charge (à l’aide de **dans**, qui est pris en charge) et comment définir et utiliser une construction .idl non défini :  
  
```  
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
  
 Ce code entraîne MYFLOT et MYDUB et *texte* entrée doit être placé dans le fichier .idl généré. Le *nom* paramètre force *texte* doit être placé avant tout ce qui fait référence à *nom* dans le fichier .idl généré. Le *dépendances* paramètre force les définitions de liste de dépendance doit être placé avant *texte* dans le fichier .idl généré.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
