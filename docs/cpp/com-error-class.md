---
title: _com_error, classe
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 093509d838ba6dc06a9b84b4c680c631a47826ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435177"
---
# <a name="comerror-class"></a>_com_error, classe

**Section spécifique à Microsoft**

Un **_com_error** objet représente une condition d’exception détectée par les fonctions de wrapper de la gestion des erreurs dans les fichiers d’en-tête générés à partir de la bibliothèque de types ou par l’une des classes de prise en charge COM. Le **_com_error** classe encapsule le code d’erreur HRESULT et associés `IErrorInfo Interface` objet.

### <a name="construction"></a>Construction

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Construit un **_com_error** objet.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](../cpp/com-error-operator-equal.md)|Assigne un existant **_com_error** objet vers un autre.|

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
|[ErrorMessage](../cpp/com-error-errormessage.md)|Récupère le message de type chaîne pour HRESULT stockées dans le **_com_error** objet.|

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

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[Interface IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)