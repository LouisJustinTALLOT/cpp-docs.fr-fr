---
title: CMemoryException, classe
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 11be0eba080085c507ed718ea23219ca1c93aeba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341185"
---
# <a name="cmemoryexception-class"></a>CMemoryException, classe

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

Aucune qualification supplémentaire n’est nécessaire ou possible. Mémoire des exceptions sont levées automatiquement par **nouveau**. Si vous écrivez vos propres fonctions de mémoire, à l’aide `malloc`, par exemple, vous êtes responsable de la levée d’exceptions de mémoire.

Pour plus d’informations sur `CMemoryException`, consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException

Construit un objet `CMemoryException`.

```
CMemoryException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais plutôt appeler la fonction globale [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Cette fonction globale peut réussir dans une situation d’insuffisance de mémoire, car il construit l’objet d’exception dans la mémoire précédemment alloué. Pour plus d’informations sur le traitement des exceptions, consultez l’article [exceptions](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[CException, classe](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)
