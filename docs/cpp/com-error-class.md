---
title: _com_error, classe
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498745"
---
# <a name="_com_error-class"></a>_com_error, classe

**Section spécifique à Microsoft**

Un objet **_com_error** représente une condition d’exception détectée par les fonctions wrapper de gestion des erreurs dans les fichiers d’en-tête générés à partir de la bibliothèque de types ou par l’une des classes de prise en charge com. La classe **_com_error** encapsule le code d’erreur HRESULT et tout `IErrorInfo Interface` objet associé.

### <a name="construction"></a>Construction

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Construit un objet **_com_error** .|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|Assigne un objet **_com_error** existant à un autre.|

### <a name="extractor-functions"></a>Extracteur, fonctions

|||
|-|-|
|[Error](../cpp/com-error-error.md)|Récupère le HRESULT passé au constructeur.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Récupère l' `IErrorInfo` objet passé au constructeur.|
|[WCode](../cpp/com-error-wcode.md)|Récupère le code d’erreur 16 bits mappé dans le HRESULT encapsulé.|

### <a name="ierrorinfo-functions"></a>Fonctions IErrorInfo

|||
|-|-|
|[Description](../cpp/com-error-description.md)|Appelle `IErrorInfo::GetDescription` la fonction.|
|[HelpContext](../cpp/com-error-helpcontext.md)|Appelle `IErrorInfo::GetHelpContext` la fonction.|
|[HelpFile](../cpp/com-error-helpfile.md)|Calls `IErrorInfo::GetHelpFile` , fonction|
|[Source](../cpp/com-error-source.md)|Appelle `IErrorInfo::GetSource` la fonction.|
|[GUID](../cpp/com-error-guid.md)|Appelle `IErrorInfo::GetGUID` la fonction.|

### <a name="format-message-extractor"></a>Format de l’extracteur de messages

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Récupère le message de type chaîne pour HRESULT stocké dans l’objet **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. wCode aux mappeurs HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mappe le HRESULT 32 bits à 16 bits `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mappe 16 bits `wCode` à HRESULT 32 bits.|

**FIN de la section spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

**En-tête:** \<ComDef. h >

`Lib:`comsuppw. lib ou comsuppwd. lib (consultez [/Zc: wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo, interface](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)