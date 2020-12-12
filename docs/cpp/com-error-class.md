---
description: 'En savoir plus sur : classe _com_error'
title: _com_error, classe
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 2d297da005feba39838679ed2b7062ce54ad9c38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318206"
---
# <a name="_com_error-class"></a>_com_error, classe

**Spécifique à Microsoft**

Un objet **_com_error** représente une condition d’exception détectée par les fonctions wrapper de gestion des erreurs dans les fichiers d’en-tête générés à partir de la bibliothèque de types ou par l’une des classes de prise en charge com. La classe **_com_error** encapsule le code d’erreur HRESULT et tout `IErrorInfo Interface` objet associé.

### <a name="construction"></a>Construction

| Nom | Description |
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Construit un objet **_com_error** .|

### <a name="operators"></a>Opérateurs

| Nom | Description |
|-|-|
|[opérateur =](../cpp/com-error-operator-equal.md)|Assigne un objet **_com_error** existant à un autre.|

### <a name="extractor-functions"></a>Extracteur, fonctions

| Nom | Description |
|-|-|
|[Error](../cpp/com-error-error.md)|Récupère le HRESULT passé au constructeur.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Récupère l' `IErrorInfo` objet passé au constructeur.|
|[WCode](../cpp/com-error-wcode.md)|Récupère le code d’erreur 16 bits mappé dans le HRESULT encapsulé.|

### <a name="ierrorinfo-functions"></a>Fonctions IErrorInfo

| Nom | Description |
|-|-|
|[Description](../cpp/com-error-description.md)|Appelle la `IErrorInfo::GetDescription` fonction.|
|[HelpContext](../cpp/com-error-helpcontext.md)|Appelle la `IErrorInfo::GetHelpContext` fonction.|
|[HelpFile](../cpp/com-error-helpfile.md)|Calls, `IErrorInfo::GetHelpFile` fonction|
|[Source](../cpp/com-error-source.md)|Appelle la `IErrorInfo::GetSource` fonction.|
|[GUID](../cpp/com-error-guid.md)|Appelle la `IErrorInfo::GetGUID` fonction.|

### <a name="format-message-extractor"></a>Format de l’extracteur de messages

| Nom | Description |
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Récupère le message de type chaîne pour HRESULT stocké dans l’objet **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. wCode aux mappeurs HRESULT

| Nom | Description |
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mappe le HRESULT 32 bits à 16 bits `wCode` .|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mappe 16 bits `wCode` à HRESULT 32 bits.|

**FIN spécifique à Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :**\<comdef.h>

`Lib:` comsuppw. lib ou comsuppwd. lib (pour plus d’informations, consultez [/Zc : wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) .

## <a name="see-also"></a>Voir aussi

[Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo, interface](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)
