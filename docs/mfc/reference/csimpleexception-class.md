---
title: Classe CSimpleException
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
ms.openlocfilehash: eb94ba9e3d26b3cd910f23c3d4abb29d3b8b1cd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318362"
---
# <a name="csimpleexception-class"></a>Classe CSimpleException

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

`CSimpleException`est la classe de base pour les exceptions de MFC critiques en ressources et gère la propriété et l’initialisation d’un message d’erreur. Les classes `CSimpleException` suivantes servent de classe de base :

|||
|-|-|
|[Classe CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Exception hors mémoire|
|[Classe D’origine CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Demandes d’une opération non étayée|
|[Classe CResourceException](../../mfc/reference/cresourceexception-class.md)|Ressource Windows non trouvée ou non crédable|
|[CUserException, classe](../../mfc/reference/cuserexception-class.md)|Exception qui indique qu’une ressource n’a pas pu être trouvée|
|[Classe CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Exception qui indique un argument invalide|

Parce `CSimpleException` que c’est une classe `CSimpleException` de base abstraite, vous ne pouvez pas déclarer un objet directement. Au lieu de cela, vous devez déclarer des objets dérivés tels que ceux du tableau précédent. Si vous déclarez votre propre classe dérivée, utilisez les classes précédentes comme modèle.

Pour plus d’informations, consultez le sujet [de la classe CException](../../mfc/reference/cexception-class.md) et [le traitement des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>CSimpleException::CSimpleException

Constructeur.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*bAutoDelete*<br/>
Spécifiez VRAI `CSimpleException` si la mémoire de l’objet a été allouée sur le tas. Cela entraînera `CSimpleException` la suppression de l’objet lorsque la fonction du `Delete` membre est appelée à supprimer l’exception. Spécifiez FALSE si l’objet `CSimpleException` est sur la pile ou est un objet global. Dans ce cas, l’objet `CSimpleException` ne `Delete` sera pas supprimé lorsque la fonction du membre est appelée.

### <a name="remarks"></a>Notes

Normalement, vous n’auriez jamais besoin d’appeler ce constructeur directement. Une fonction qui jette une exception devrait `CException`créer une instance d’une classe dérivée et appeler son constructeur, ou elle devrait utiliser l’une des fonctions de lancement MFC, telles que [AfxThrowFileException](exception-processing.md#afxthrowfileexception), pour lancer un type prédéfini.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>CSimpleException::GetErrorMessage

Appelez cette fonction de membre pour fournir du texte au sujet d’une erreur qui s’est produite.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszError*<br/>
Un pointeur vers un tampon qui recevra un message d’erreur.

*nMaxError (en)*<br/>
Le nombre maximum de caractères que le tampon peut contenir, y compris le terminateur NULL.

*pnHelpContext*<br/>
L’adresse d’un UINT qui recevra l’ID contexte d’aide. Si NULL, aucune pièce d’identité ne sera retournée.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0 si aucun texte de message d’erreur n’est disponible.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Gestion des exceptions](../../mfc/exception-handling-in-mfc.md)
