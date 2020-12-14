---
description: 'En savoir plus sur : classe CUserException'
title: CUserException, classe
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 6104aa2883a80f88aed03634f09ad1947e9c6794
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344963"
---
# <a name="cuserexception-class"></a>CUserException, classe

Levée pour arrêter une opération d'utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>Notes

Utilisez `CUserException` lorsque vous souhaitez utiliser le mécanisme d’exception Throw/catch pour les exceptions spécifiques à l’application. « User » dans le nom de la classe peut être interprété comme « mon utilisateur a fait des choses exceptionnellement que je dois gérer ».

Une `CUserException` est généralement levée après l’appel de la fonction globale `AfxMessageBox` pour informer l’utilisateur qu’une opération a échoué. Lorsque vous écrivez un gestionnaire d’exceptions, gérez l’exception de façon spéciale, car l’utilisateur a généralement été informé de l’échec. Dans certains cas, l’infrastructure lève cette exception. Pour lever une `CUserException` vous-même, avertissez l’utilisateur, puis appelez la fonction globale `AfxThrowUserException` .

Dans l’exemple ci-dessous, une fonction qui contient des opérations qui peuvent échouer avertit l’utilisateur et lève une `CUserException` . La fonction appelante intercepte l’exception et la gère spécialement :

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

Pour plus d’informations sur l’utilisation de `CUserException` , consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CException (classe)](../../mfc/reference/cexception-class.md)
