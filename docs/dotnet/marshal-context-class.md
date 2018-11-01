---
title: marshal_context, classe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_context
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 0e25aee0996b0cd16ca92566da22d377b762d7bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594530"
---
# <a name="marshalcontext-class"></a>marshal_context, classe

Cette classe convertit des données entre les environnements natifs et managés.

## <a name="syntax"></a>Syntaxe

```
class marshal_context
```

## <a name="remarks"></a>Notes

Utilisez la `marshal_context` classe pour les conversions de données qui requièrent un contexte. Consultez [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur les conversions nécessitent un contexte et quel fichier marshaling doit être inclus. Le résultat du marshaling lorsque vous utilisez un contexte est valide uniquement jusqu'à la `marshal_context` objet est détruit. Pour conserver votre résultat, vous devez copier les données.

Le même `marshal_context` peut être utilisé pour plusieurs conversions de données. Réutiliser le contexte de cette manière n’affecteront pas les résultats des appels de marshaling précédents.

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, ou \<msclr\marshal_atl.h >

**Namespace :** msclr::interop

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)