---
title: 'marshal_context :: ~ marshal_context | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 49f194f153f3e4f911333e22b11ebddf7efcaa32
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447256"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context

Détruit un objet `marshal_context`.

## <a name="syntax"></a>Syntaxe

```
~marshal_context();
```

## <a name="remarks"></a>Notes

Certaines conversions de données nécessitent un contexte de marshaler. Consultez [vue d’ensemble du Marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur les traductions nécessitent un contexte et quel fichier marshaling doit être inclus dans votre application.

Suppression d’un `marshal_context` objet invalidera les données converties par ce contexte. Si vous souhaitez conserver vos données après un `marshal_context` objet est détruit, vous devez copier manuellement les données à une variable qui est conservé.

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, ou \<msclr\marshal_atl.h >

**Namespace :** msclr::interop

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)