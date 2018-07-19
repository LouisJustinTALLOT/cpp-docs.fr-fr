---
title: _com_error, classe | Microsoft Docs
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
ms.openlocfilehash: 0d59782b62ddfb51601505be6d12f01ce14cd4f1
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026632"
---
# <a name="comerror-class"></a>_com_error, classe
**Section spécifique à Microsoft**  
  
 Un `_com_error` objet représente une condition d’exception détectée par les fonctions de wrapper de la gestion des erreurs dans les fichiers d’en-tête générés à partir de la bibliothèque de types ou par l’une des classes de prise en charge COM. Le `_com_error` classe encapsule le code d’erreur HRESULT et associés `IErrorInfo Interface` objet.  
  
### <a name="construction"></a>Construction  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|Construit un objet `_com_error`.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[opérateur =](../cpp/com-error-operator-equal.md)|Assigne un objet `_com_error` existant à un autre.|  
  
### <a name="extractor-functions"></a>Fonctions d’extracteur  
  
|||  
|-|-|  
|[Error](../cpp/com-error-error.md)|Récupère la valeur HRESULT passé au constructeur.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Récupère le `IErrorInfo` objet passé au constructeur.|  
|[WCode](../cpp/com-error-wcode.md)|Récupère le code d’erreur 16 bits mappé dans la valeur HRESULT encapsulé.|  
  
### <a name="ierrorinfo-functions"></a>Fonctions de IErrorInfo  
  
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
|[ErrorMessage](../cpp/com-error-errormessage.md)|Récupère le message de type chaîne pour HRESULT stockées dans le `_com_error` objet.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode dans les mappeurs HRESULT  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mappe le HRESULT de 32 bits à 16 bits `wCode`.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mappe les 16 bits `wCode` vers HRESULT de 32 bits.|  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<comdef.h >  
  
 `Lib:` comsuppw.lib ou comsuppwd.lib (voir [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)   
 [Interface IErrorInfo](http://msdn.microsoft.com/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)