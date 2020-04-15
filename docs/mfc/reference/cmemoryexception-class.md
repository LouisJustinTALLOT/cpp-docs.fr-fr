---
title: Classe CMemoryException
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 375b4227a25ae4c18cfd263eff4c3ec13f1304e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370010"
---
# <a name="cmemoryexception-class"></a>Classe CMemoryException

Représente une condition d'exception liée à une insuffisance de mémoire.

## <a name="syntax"></a>Syntaxe

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Construit un objet `CMemoryException`.|

## <a name="remarks"></a>Notes

Aucune autre qualification n’est nécessaire ou possible. Les exceptions de mémoire sont lancées automatiquement par **de nouveaux**. Si vous écrivez vos propres `malloc`fonctions de mémoire, en utilisant, par exemple, alors vous êtes responsable de jeter des exceptions de mémoire.

Pour plus `CMemoryException`d’informations sur , voir l’article [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException::CMemoryException

Construit un objet `CMemoryException`.

```
CMemoryException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). cette fonction globale peut réussir dans une situation hors mémoire parce qu’elle construit l’objet d’exception dans la mémoire précédemment allouée. pour plus d’informations sur le traitement des exceptions, voir les [exceptions](../exception-handling-in-mfc.md)de l’article .

## <a name="see-also"></a>Voir aussi

[Classe CException](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)
