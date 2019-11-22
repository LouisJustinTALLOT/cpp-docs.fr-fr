---
title: Initialisation et terminaison du moteur de base de données DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 24a24d5a81da18d01472fc760c2adf96ee9868d5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303458"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète. Lorsque vous utilisez des objets DAO MFC, le moteur de base de données DAO doit d’abord être initialisé, puis se terminer avant la fermeture de votre application ou de votre DLL. Deux fonctions, `AfxDaoInit` et `AfxDaoTerm`, effectuent ces tâches.

### <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Initialise le moteur de base de données DAO.|
|[AfxDaoTerm](#afxdaoterm)|Termine le moteur de base de données DAO.|

##  <a name="afxdaoinit"></a>  AfxDaoInit

Cette fonction initialise le moteur de base de données DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’avez pas besoin d’appeler `AfxDaoInit`, car l’application l’appelle automatiquement quand cela est nécessaire.

Pour obtenir des informations connexes et pour obtenir un exemple d’appel de `AfxDaoInit`, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Conditions requises

  **En-tête** afxdao. h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Cette fonction termine le moteur de base de données DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Notes

En règle générale, vous devez appeler cette fonction uniquement dans une DLL MFC normale ; une application appellera automatiquement `AfxDaoTerm` lorsque cela est nécessaire.

Dans les DLL MFC normales, appelez `AfxDaoTerm` avant la fonction `ExitInstance`, mais une fois que tous les objets DAO de MFC ont été détruits.

Pour obtenir des informations connexes, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Conditions requises

  **En-tête** afxdao. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
