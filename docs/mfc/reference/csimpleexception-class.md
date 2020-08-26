---
title: CSimpleException, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: afd83c1ddd6f68b10c5cc8c47c0e939bbd01b6c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840711"
---
# <a name="csimpleexception-class"></a>CSimpleException, classe

Cette classe est une classe de base pour les exceptions MFC critiques pour les ressources.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|Fournit du texte sur une erreur qui s’est produite.|

## <a name="remarks"></a>Notes

`CSimpleException` est la classe de base pour les exceptions MFC critiques pour les ressources et gère la propriété et l’initialisation d’un message d’erreur. Les classes suivantes utilisent `CSimpleException` comme classe de base :

|Nom|Description|
|-|-|
|[CMemoryException, classe](../../mfc/reference/cmemoryexception-class.md)|Exception de mémoire insuffisante|
|[CNotSupportedException, classe](../../mfc/reference/cnotsupportedexception-class.md)|Demandes pour une opération non prise en charge|
|[CResourceException, classe](../../mfc/reference/cresourceexception-class.md)|Ressource Windows introuvable ou non pouvant être créée|
|[CUserException, classe](../../mfc/reference/cuserexception-class.md)|Exception qui indique qu’une ressource est introuvable|
|[CInvalidArgException, classe](../../mfc/reference/cinvalidargexception-class.md)|Exception qui indique un argument non valide|

Étant donné que `CSimpleException` est une classe de base abstraite, vous ne pouvez pas déclarer `CSimpleException` directement un objet. Au lieu de cela, vous devez déclarer des objets dérivés tels que ceux du tableau précédent. Si vous déclarez votre propre classe dérivée, utilisez les classes précédentes comme modèle.

Pour plus d’informations, consultez la rubrique relative à la [classe CException](../../mfc/reference/cexception-class.md) et la [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Configuration requise

**En-tête :** AFX. h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a> CSimpleException::CSimpleException

Constructeur.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*bAutoDelete*<br/>
Spécifiez TRUE si la mémoire de l' `CSimpleException` objet a été allouée sur le tas. Cela entraîne la suppression de l' `CSimpleException` objet lorsque la `Delete` fonction membre est appelée pour supprimer l’exception. Spécifiez FALSe si l' `CSimpleException` objet se trouve sur la pile ou s’il s’agit d’un objet global. Dans ce cas, l' `CSimpleException` objet n’est pas supprimé lorsque la `Delete` fonction membre est appelée.

### <a name="remarks"></a>Notes

Normalement, vous n’avez jamais besoin d’appeler ce constructeur directement. Une fonction qui lève une exception doit créer une instance d’une `CException` classe dérivée de et appeler son constructeur, ou elle doit utiliser l’une des fonctions de levée MFC, telles que [AfxThrowFileException](exception-processing.md#afxthrowfileexception), pour lever un type prédéfini.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a> CSimpleException::GetErrorMessage

Appelez cette fonction membre pour fournir du texte sur une erreur qui s’est produite.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszError*<br/>
Pointeur vers une mémoire tampon qui reçoit un message d’erreur.

*nMaxError*<br/>
Nombre maximal de caractères que la mémoire tampon peut contenir, y compris la marque de fin NULL.

*pnHelpContext*<br/>
Adresse d’un UINT qui recevra l’ID de contexte d’aide. Si la valeur est NULL, aucun ID n’est retourné.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction réussit ; Sinon, 0 si aucun texte de message d’erreur n’est disponible.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [CException :: GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CException (classe)](../../mfc/reference/cexception-class.md)<br/>
[Gestion des exceptions](../../mfc/exception-handling-in-mfc.md)
