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
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855290"
---
# <a name="carchiveexception-class"></a>CArchiveException, classe

Représente une condition d’exception de sérialisation

## <a name="syntax"></a>Syntaxe

```
class CArchiveException : public CException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Construit un objet `CArchiveException`.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[CArchiveException :: m_cause](#m_cause)|Indique la cause de l’exception.|
|[CArchiveException :: m_strFileName](#m_strfilename)|Spécifie le nom du fichier pour cette condition d’exception.|

## <a name="remarks"></a>Notes 

La classe `CArchiveException` comprend un membre de données public qui indique la cause de l’exception.

les objets `CArchiveException` sont construits et levés à l’intérieur des fonctions membres [CArchive](../../mfc/reference/carchive-class.md) . Vous pouvez accéder à ces objets dans l’étendue d’une expression **catch** . Le code de cause est indépendant du système d’exploitation. Pour plus d’informations sur le traitement des exceptions, consultez [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="carchiveexception"></a>CArchiveException::CArchiveException

Construit un objet `CArchiveException`, en stockant la valeur de la *cause* dans l’objet.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Variable de type énuméré qui indique la raison de l’exception. Pour obtenir la liste des énumérateurs, consultez le [m_cause](#m_cause) membre de données.

*lpszArchiveName*<br/>
Pointe vers une chaîne contenant le nom de l’objet `CArchive` à l’origine de l’exception.

### <a name="remarks"></a>Notes 

Vous pouvez créer un objet `CArchiveException` sur le tas et le lever vous-même ou laisser la fonction globale [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) la gérer pour vous.

N’utilisez pas ce constructeur directement. au lieu de cela, appelez la fonction globale `AfxThrowArchiveException`.

##  <a name="m_cause"></a>CArchiveException :: m_cause

Spécifie la cause de l’exception.

```
int m_cause;
```

### <a name="remarks"></a>Notes 

Ce membre de données est une variable publique de type **int**. Ses valeurs sont définies par un `CArchiveException` type énuméré. Voici les énumérateurs et leurs significations :

- `CArchiveException::none` aucune erreur ne s’est produite.

- `CArchiveException::genericException` erreur non spécifiée.

- `CArchiveException::readOnly` essayé d’écrire dans une archive ouverte pour le chargement.

- `CArchiveException::endOfFile` atteint la fin du fichier lors de la lecture d’un objet.

- `CArchiveException::writeOnly` essayé de lire à partir d’une archive ouverte pour le stockage.

- `CArchiveException::badIndex` format de fichier non valide.

- `CArchiveException::badClass` essayé de lire un objet dans un objet de type incorrect.

- `CArchiveException::badSchema` essayé de lire un objet avec une version différente de la classe.

    > [!NOTE]
    >  Ces énumérateurs de cause `CArchiveException` sont distincts des énumérateurs de cause `CFileException`.

    > [!NOTE]
    > `CArchiveException::generic` est déconseillé. Utilisez `genericException` à la place. Si le **générique** est utilisé dans une application et généré avec/CLR, il y aura des erreurs de syntaxe qui ne sont pas faciles à déchiffrer.

##  <a name="m_strfilename"></a>CArchiveException :: m_strFileName

Spécifie le nom du fichier pour cette condition d’exception.

```
CString m_strFileName;
```

## <a name="see-also"></a>Voir aussi

[CException, classe](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CArchive, classe](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Traitement des exceptions](../../mfc/reference/exception-processing.md)
