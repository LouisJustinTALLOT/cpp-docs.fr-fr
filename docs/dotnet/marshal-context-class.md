---
title: marshal_context, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6bf712e960cbf96ccef6c3a3e4efebdad9045818
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136992"
---
# <a name="marshalcontext-class"></a>marshal_context, classe
Cette classe convertit les données entre les environnements natifs et managés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class marshal_context  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez la `marshal_context` classe pour les conversions de données qui requièrent un contexte. Consultez [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur les conversions nécessitent un contexte et le marshaling du fichier doit être inclus. Le résultat du marshaling lorsque vous utilisez un contexte est valide uniquement jusqu'à la `marshal_context` objet est détruit. Pour conserver votre résultat, vous devez copier les données.  
  
 Le même `marshal_context` peut être utilisé pour plusieurs conversions de données. Réutiliser le contexte de cette manière n’affecte pas les résultats des appels précédents de marshaling.  
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, ou \<msclr\marshal_atl.h >  
  
 **Namespace :** msclr::interop  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)