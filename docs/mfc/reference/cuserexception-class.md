---
title: Cuserexception, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71d2be1c00e518597a5d5121d7a53544bd29067f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419657"
---
# <a name="cuserexception-class"></a>Cuserexception, classe

Levée pour arrêter une opération d'utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>Notes

Utilisez `CUserException` lorsque vous souhaitez utiliser le mécanisme d’exception throw/catch pour les exceptions spécifiques à l’application. « Utilisateur » dans le nom de classe peut être interprétée comme « mon utilisateur a fait quelque chose d’exceptionnel que je dois gérer. »

Un `CUserException` est généralement levée après l’appel de la fonction globale `AfxMessageBox` pour avertir l’utilisateur qu’une opération a échoué. Lorsque vous écrivez un gestionnaire d’exceptions, gérer l’exception spécialement dans la mesure où l’utilisateur généralement a déjà été informé de l’échec. Le framework lève cette exception dans certains cas. Pour lever une `CUserException` vous-même, alerter l’utilisateur et appelle ensuite la fonction globale `AfxThrowUserException`.

Dans l’exemple ci-dessous, une fonction contenant des opérations qui risquent d’échouer avertit l’utilisateur et lève un `CUserException`. La fonction appelante intercepte l’exception et il gère spécialement :

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

Pour plus d’informations sur l’utilisation de `CUserException`, consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CException, classe](../../mfc/reference/cexception-class.md)
