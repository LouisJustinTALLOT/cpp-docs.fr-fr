---
description: 'En savoir plus sur : DAO Moteur de base de données l’initialisation et l’arrêt'
title: Initialisation et terminaison du moteur de base de données DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 9e9b522d744eabc84074b201051151b80ed75d7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220394"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète. Lorsque vous utilisez des objets DAO MFC, le moteur de base de données DAO doit d’abord être initialisé, puis se terminer avant la fermeture de votre application ou de votre DLL. Deux fonctions, `AfxDaoInit` et `AfxDaoTerm` , exécutent ces tâches.

### <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO

|Nom|Description|
|-|-|
|[AfxDaoInit](#afxdaoinit)|Initialise le moteur de base de données DAO.|
|[AfxDaoTerm](#afxdaoterm)|Termine le moteur de base de données DAO.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a> AfxDaoInit

Cette fonction initialise le moteur de base de données DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’avez pas besoin d’appeler `AfxDaoInit` , car l’application l’appelle automatiquement quand cela est nécessaire.

Pour obtenir des informations connexes et pour obtenir un exemple d’appel `AfxDaoInit` , consultez la [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a> AfxDaoTerm

Cette fonction termine le moteur de base de données DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Notes

En règle générale, vous devez appeler cette fonction uniquement dans une DLL MFC normale ; une application appelle automatiquement `AfxDaoTerm` quand elle est nécessaire.

Dans les DLL MFC normales, appelez `AfxDaoTerm` avant la `ExitInstance` fonction, mais une fois que tous les objets DAO de MFC ont été détruits.

Pour obtenir des informations connexes, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
