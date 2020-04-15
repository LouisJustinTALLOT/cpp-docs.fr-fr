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
ms.openlocfilehash: ad2a9d8c5b4466a04b5a88fcce7679911bf1b81a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377015"
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
|[CArchiveException::m_cause](#m_cause)|Indique la cause d’exception.|
|[CArchiveException::m_strFileName](#m_strfilename)|Spécifie le nom du fichier pour cette condition d’exception.|

## <a name="remarks"></a>Notes

Le `CArchiveException` groupe comprend un membre public des données qui indique la cause de l’exception.

`CArchiveException`objets sont construits et jetés à l’intérieur des fonctions des membres [CArchive.](../../mfc/reference/carchive-class.md) Vous pouvez accéder à ces objets dans le cadre d’une expression **CATCH.** Le code de cause est indépendant du système d’exploitation. Pour plus d’informations sur le traitement des exceptions, voir [Traitement d’exception (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

Construit un `CArchiveException` objet, stockant la valeur de *la cause* dans l’objet.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Une variable de type énuméré qui indique la raison de l’exception. Pour une liste des enumérateurs, consultez le [m_cause](#m_cause) membre des données.

*lpszArchiveName (en)*<br/>
Indique une chaîne contenant le `CArchive` nom de l’objet causant l’exception.

### <a name="remarks"></a>Notes

Vous pouvez `CArchiveException` créer un objet sur le tas et le jeter vous-même ou laisser la fonction globale [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) le gérer pour vous.

N’utilisez pas ce constructeur directement; au lieu de `AfxThrowArchiveException`cela, appelez la fonction globale .

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException::m_cause

Spécifie la cause de l’exception.

```
int m_cause;
```

### <a name="remarks"></a>Notes

Ce membre de données est une variable publique de type **int**. Ses valeurs sont `CArchiveException` définies par un type énuméré. Voici les énumérateurs et leurs significations :

- `CArchiveException::none`Aucune erreur ne s’est produite.

- `CArchiveException::genericException`Erreur non spécifiée.

- `CArchiveException::readOnly`Essayé d’écrire dans une archive ouverte pour le chargement.

- `CArchiveException::endOfFile`Atteint la fin du fichier en lisant un objet.

- `CArchiveException::writeOnly`Essayé de lire à partir d’une archive ouverte pour le stockage.

- `CArchiveException::badIndex`Format de fichier invalide.

- `CArchiveException::badClass`Essayé de lire un objet dans un objet du mauvais type.

- `CArchiveException::badSchema`Essayé de lire un objet avec une version différente de la classe.

    > [!NOTE]
    >  Ces énumérateurs de cause `CArchiveException` sont distincts des énumérateurs de cause `CFileException`.

    > [!NOTE]
    > `CArchiveException::generic` est déconseillé. Utilisez `genericException` à la place. Si **le générique** est utilisé dans une application et construit avec /clr, il y aura des erreurs de syntaxe qui ne sont pas faciles à déchiffrer.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException::m_strFileName

Spécifie le nom du fichier pour cette condition d’exception.

```
CString m_strFileName;
```

## <a name="see-also"></a>Voir aussi

[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CArchive, classe](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Traitement des exceptions](../../mfc/reference/exception-processing.md)
