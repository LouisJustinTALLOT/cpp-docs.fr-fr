---
title: emitidl | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.emitidl
dev_langs: C++
helpviewer_keywords: emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 09174362718c8e8efd30f901394650fbbb5ebf63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="emitidl"></a>emitidl
Spécifie si tous les attributs IDL suivantes sont traitées et placées dans le fichier .idl généré.  
  
## <a name="syntax"></a>Syntaxe  
  
```
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>Paramètres  
*state*  
Une de ces valeurs possibles : **true**, **false**, **forcé**, **restreint**, **push**, ou **pop**.  
  
-   Si **true**, les attributs de catégorie IDL rencontrées dans un fichier de code source sont placées dans le fichier .idl généré. Il s’agit du paramètre par défaut **emitidl**.  
  
-   Si **false**, les attributs de catégorie IDL rencontrées dans un fichier de code source ne sont pas placés dans le fichier .idl généré.  
  
-   Si **restreint**, permet des attributs IDL dans le fichier sans un [module](../windows/module-cpp.md) attribut. Le compilateur ne génère pas un fichier .idl.  
  
-   Si **forcé**, remplace une ultérieure **restreint** attribut, ce qui nécessite un fichier d’avoir un **module** attribut s’il n’y IDL d’attributs dans le fichier.  
  
-   **push** vous permet d’enregistrer l’actuel **emitidl** paramètres interne **emitidl** pile, et **pop** vous permet de définir **emitidl**à la valeur est en haut de la liste interne **emitidl** pile.  
  
`defaultimports=`*Boolean* \(facultatif)  
-   Si *booléenne* est **true**, docobj.idl est importé dans le fichier .idl généré. En outre, si un fichier .idl avec le même nom qu’un .h `#include` dans votre source de code se trouve dans le même répertoire que le fichier .h, puis le fichier .idl généré contient une instruction d’importation pour ce fichier .idl.  
  
-   Si *booléenne* est **false**, docobj.idl n’est pas importé dans le fichier .idl généré. Vous devez importer explicitement les fichiers .idl avec [importer](../windows/import.md).  
  
## <a name="remarks"></a>Remarques  
Après le **emitidl** attribut C++ est rencontré dans un fichier de code source, les attributs de catégorie IDL sont placés dans le fichier .idl généré. S’il existe aucune **emitidl** attribut, les attributs IDL dans le fichier de code source s’affichent dans le fichier .idl généré.  
  
Il est possible d’avoir plusieurs **emitidl** attributs dans un fichier de code source. Si `[emitidl(false)];` est rencontré dans un fichier sans une ultérieure `[emitidl(true)];`, pas d’attributs sont traitées dans le fichier .idl généré.  
  
Chaque fois que le compilateur rencontre un nouveau fichier, **emitidl** a implicitement la valeur **true**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|None|  
  
Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
[Attributs du compilateur](../windows/compiler-attributes.md)   
[Attributs autonomes](../windows/stand-alone-attributes.md)   
[Exemples d’attributs](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)