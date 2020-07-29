---
title: CArchiveException, classe
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 68f64cfd7dc96da04fcc0945a6b996eab4101487
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231882"
---
# <a name="carchiveexception-class"></a>CArchiveException, classe

Représente une condition d’exception de sérialisation

## <a name="syntax"></a>Syntaxe

```
class CArchiveException : public CException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Construit un objet `CArchiveException`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CArchiveException :: m_cause](#m_cause)|Indique la cause de l’exception.|
|[CArchiveException :: m_strFileName](#m_strfilename)|Spécifie le nom du fichier pour cette condition d’exception.|

## <a name="remarks"></a>Notes

La `CArchiveException` classe comprend un membre de données public qui indique la cause de l’exception.

`CArchiveException`les objets sont construits et levés à l’intérieur des fonctions membres [CArchive](../../mfc/reference/carchive-class.md) . Vous pouvez accéder à ces objets dans l’étendue d’une expression **catch** . Le code de cause est indépendant du système d’exploitation. Pour plus d’informations sur le traitement des exceptions, consultez [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

Construit un `CArchiveException` objet, en stockant la valeur de *cause* dans l’objet.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Paramètres

*bloquer*<br/>
Variable de type énuméré qui indique la raison de l’exception. Pour obtenir la liste des énumérateurs, consultez le [m_cause](#m_cause) membre de données.

*lpszArchiveName*<br/>
Pointe vers une chaîne contenant le nom de l' `CArchive` objet à l’origine de l’exception.

### <a name="remarks"></a>Notes

Vous pouvez créer un `CArchiveException` objet sur le tas et le lever vous-même ou laisser la fonction globale [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) la gérer pour vous.

N’utilisez pas ce constructeur directement. au lieu de cela, appelez la fonction globale `AfxThrowArchiveException` .

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException :: m_cause

Spécifie la cause de l’exception.

```
int m_cause;
```

### <a name="remarks"></a>Notes

Ce membre de données est une variable publique de type **`int`** . Ses valeurs sont définies par un `CArchiveException` type énuméré. Voici les énumérateurs et leurs significations :

- `CArchiveException::none`Aucune erreur ne s’est produite.

- `CArchiveException::genericException`Erreur non spécifiée.

- `CArchiveException::readOnly`Tentative d’écriture dans une archive ouverte pour le chargement.

- `CArchiveException::endOfFile`Fin de fichier atteinte lors de la lecture d’un objet.

- `CArchiveException::writeOnly`Tentative de lecture à partir d’une archive ouverte pour le stockage.

- `CArchiveException::badIndex`Format de fichier non valide.

- `CArchiveException::badClass`Tentative de lecture d’un objet dans un objet de type incorrect.

- `CArchiveException::badSchema`Tentative de lecture d’un objet avec une version différente de la classe.

    > [!NOTE]
    >  Ces énumérateurs de cause `CArchiveException` sont distincts des énumérateurs de cause `CFileException`.

    > [!NOTE]
    > `CArchiveException::generic` est déconseillé. Utilisez `genericException` à la place. Si le **générique** est utilisé dans une application et généré avec/CLR, il y aura des erreurs de syntaxe qui ne sont pas faciles à déchiffrer.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException :: m_strFileName

Spécifie le nom du fichier pour cette condition d’exception.

```
CString m_strFileName;
```

## <a name="see-also"></a>Voir aussi

[CException (classe)](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CArchive (classe)](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Traitement des exceptions](../../mfc/reference/exception-processing.md)
