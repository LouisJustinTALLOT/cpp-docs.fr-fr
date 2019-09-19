---
title: Initialisation et terminaison du moteur de base de données DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: ccdf2e7b0f31576dddccad016e6b32806cdb82bf
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095878"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. 3,6 est la version finale et est considérée comme obsolète. Lorsque vous utilisez des objets DAO MFC, le moteur de base de données DAO doit d’abord être initialisé, puis se terminer avant la fermeture de votre application ou de votre DLL. Deux fonctions, `AfxDaoInit` et `AfxDaoTerm`, exécutent ces tâches.

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

Dans la plupart des cas, vous n’avez `AfxDaoInit` pas besoin d’appeler, car l’application l’appelle automatiquement quand cela est nécessaire.

Pour obtenir des informations connexes et pour obtenir un exemple `AfxDaoInit`d’appel, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao. h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Cette fonction termine le moteur de base de données DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Notes

En règle générale, vous devez appeler cette fonction uniquement dans une DLL MFC normale ; une application appelle `AfxDaoTerm` automatiquement quand elle est nécessaire.

Dans les DLL MFC normales, `AfxDaoTerm` appelez avant `ExitInstance` la fonction, mais une fois que tous les objets DAO de MFC ont été détruits.

Pour obtenir des informations connexes, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
