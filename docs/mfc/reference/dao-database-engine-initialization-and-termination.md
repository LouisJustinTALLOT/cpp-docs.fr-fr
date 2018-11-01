---
title: Initialisation et terminaison du moteur de base de données DAO
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.data
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: ff924f0e0d599d447ef7dea0039de788d388d759
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589629"
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
