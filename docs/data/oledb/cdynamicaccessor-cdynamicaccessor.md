---
title: CDynamicAccessor::CDynamicAccessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class, constructor
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ce33fd4aa64114a0b4465bb3272f74ef2ccf8258
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessorcdynamicaccessor"></a>CDynamicAccessor::CDynamicAccessor
Instancie et initialise le `CDynamicAccessor` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `eBlobHandling`  
 Spécifie la façon dont les données d’objet binaire volumineux (BLOB) doit être gérée. La valeur par défaut est **DBBLOBHANDLING_DEFAULT**. Consultez [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) pour obtenir une description de la **DBBLOBHANDLINGENUM** valeurs.  
  
 `nBlobSize`  
 La taille maximale de BLOB en octets ; données de la colonne sur cette valeur sont traitées comme un objet BLOB. La valeur par défaut est 8 000 caractères. Consultez [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) pour plus d’informations.  
  
## <a name="remarks"></a>Notes  
 Si vous utilisez le constructeur pour initialiser le `CDynamicAccessor` de l’objet, vous pouvez spécifier comment il liera des objets BLOB. Objets BLOB peut contenir des données binaires telles que des graphiques, audio ou des codes compilés. Le comportement par défaut consiste à traiter les colonnes dépasse 8 000 octets en tant qu’objets BLOB et essayez de les lier à un `ISequentialStream` objet. Toutefois, vous pouvez spécifier une valeur différente pour la taille de l’objet BLOB.  
  
 Vous pouvez également spécifier comment `CDynamicAccessor` gère les données de colonne sont des données d’objet BLOB : il peut gérer des données BLOB dans la méthode par défaut ; il peut ignorer (ne pas lier) les données BLOB ; ou il pouvez lier des données d’objet BLOB dans la mémoire allouée par le fournisseur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)