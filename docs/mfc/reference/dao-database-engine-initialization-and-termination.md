---
title: Initialisation et terminaison du moteur de base de données DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 62460e8e55f70b8cb0743f1d044636d25121050d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365892"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

DAO est utilisé avec les bases de données Access et est pris en charge par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète. Lors de l’utilisation d’objets MFC DAO, le moteur de base de données DAO doit d’abord être para initialisé, puis terminé avant que votre application ou DLL démissionne. Deux `AfxDaoInit` fonctions, `AfxDaoTerm`et , effectuer ces tâches.

### <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Initialise le moteur de base de données DAO.|
|[AfxDaoTerm](#afxdaoterm)|Termine le moteur de base de données DAO.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a>AfxDaoInit AfxDaoInit

Cette fonction est para initialisée par le moteur de base de données DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, `AfxDaoInit` vous n’avez pas besoin d’appeler parce que l’application l’appelle automatiquement quand il est nécessaire.

Pour obtenir des informations connexes, `AfxDaoInit`et pour un exemple d’appel, voir [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a>AfxDaoTerm

Cette fonction met fin au moteur de base de données DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Notes

Typiquement, vous n’avez qu’à appeler cette fonction dans un DLL MFC régulier; une application appellera `AfxDaoTerm` automatiquement quand elle est nécessaire.

Dans les DLL MFC réguliers, appelez `AfxDaoTerm` avant la `ExitInstance` fonction, mais après que tous les objets MFC DAO ont été détruits.

Pour plus d’informations connexes, voir [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
