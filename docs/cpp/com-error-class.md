---
title: classe _com_error | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95550c81235db58b1f8d372bf028750c003c7a9f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415723"
---
# <a name="comerror-class"></a>_com_error, classe
**Section spécifique à Microsoft**  
  
 A `_com_error` objet représente une condition d’exception détectée par les fonctions wrapper de gestion des erreurs dans les fichiers d’en-tête générés à partir de la bibliothèque de types ou par une des classes de prise en charge COM. Le `_com_error` classe encapsule le `HRESULT` code d’erreur et associés `IErrorInfo Interface` objet.  
  
### <a name="construction"></a>Construction  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|Construit un objet `_com_error`.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[opérateur =](../cpp/com-error-operator-equal.md)|Assigne un objet `_com_error` existant à un autre.|  
  
### <a name="extractor-functions"></a>Fonctions d’extraction  
  
|||  
|-|-|  
|[Error](../cpp/com-error-error.md)|Extrait le `HRESULT` transmis au constructeur.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Récupère le `IErrorInfo` objet passé au constructeur.|  
|[WCode](../cpp/com-error-wcode.md)|Récupère le code d'erreur 16 bits mappé dans le `HRESULT` encapsulé.|  
  
### <a name="ierrorinfo-functions"></a>Fonctions d’IErrorInfo  
  
|||  
|-|-|  
|[Description](../cpp/com-error-description.md)|Appels `IErrorInfo::GetDescription` (fonction).|  
|[HelpContext](../cpp/com-error-helpcontext.md)|Appels `IErrorInfo::GetHelpContext` (fonction).|  
|[HelpFile](../cpp/com-error-helpfile.md)|Appels `IErrorInfo::GetHelpFile` (fonction)|  
|[Source](../cpp/com-error-source.md)|Appels `IErrorInfo::GetSource` (fonction).|  
|[GUID](../cpp/com-error-guid.md)|Appels `IErrorInfo::GetGUID` (fonction).|  
  
### <a name="format-message-extractor"></a>Extracteur de Message de format  
  
|||  
|-|-|  
|[ErrorMessage](../cpp/com-error-errormessage.md)|Récupère le message de chaîne pour HRESULT est stockée dans le `_com_error` objet.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode à mappeurs de HRESULT  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mappe les 32 bits `HRESULT` à 16 bits `wCode`.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mappe `wCode` 16 bits vers `HRESULT` 32 bits.|  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<comdef.h >  
  
 `Lib:` comsuppw.lib ou comsuppwd.lib (consultez [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)   
 [Interface IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)