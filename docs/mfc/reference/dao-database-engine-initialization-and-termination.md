---
title: L’initialisation du moteur de base de données DAO et d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf54992896559f1b143247746ef9f9e0e8d8979
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404005"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

Lorsque vous utilisez des objets DAO de MFC, le moteur de base de données DAO doit d’abord être initialisé et puis interrompue avant la fermeture de votre application ou une DLL. Deux fonctions, `AfxDaoInit` et `AfxDaoTerm`, effectuer ces tâches.

### <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Initialise le moteur de base de données DAO.|
|[AfxDaoTerm](#afxdaoterm)|Arrête le moteur de base de données DAO.|

##  <a name="afxdaoinit"></a>  AfxDaoInit

Cette fonction initialise le moteur de base de données DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’avez pas besoin d’appeler `AfxDaoInit` , car l’application qu’il appelle automatiquement lorsqu’il est nécessaire.

Pour plus d’informations et pour obtenir un exemple de l’appel `AfxDaoInit`, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Cette fonction termine le moteur de base de données DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Notes

En règle générale, vous devez uniquement appeler cette fonction dans un DLL MFC ; normal une application appelle automatiquement `AfxDaoTerm` quand il est nécessaire.

Dans les DLL MFC normales, appelez `AfxDaoTerm` avant le `ExitInstance` (fonction), mais une fois que tous les objets DAO de MFC ont été détruits.

Pour plus d’informations, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
