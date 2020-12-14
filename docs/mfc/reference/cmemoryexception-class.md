---
description: 'En savoir plus sur : classe CMemoryException'
title: CMemoryException, classe
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 694629d65c8b4cffc351873d5da3d8ed3c34cf8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336658"
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
|[CMemoryException :: CMemoryException](#cmemoryexception)|Construit un objet `CMemoryException`.|

## <a name="remarks"></a>Notes

Aucune qualification supplémentaire n’est nécessaire ou possible. Les exceptions de mémoire sont levées automatiquement par **`new`** . Si vous écrivez vos propres fonctions mémoire à l’aide `malloc` de, par exemple, vous êtes responsable de la levée des exceptions de mémoire.

Pour plus d’informations sur `CMemoryException` , consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a> CMemoryException :: CMemoryException

Construit un objet `CMemoryException`.

```
CMemoryException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Cette fonction globale peut être correctement exécutée dans une situation de mémoire insuffisante, car elle construit l’objet exception dans la mémoire précédemment allouée. Pour plus d’informations sur le traitement des exceptions, consultez l’article [exceptions](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[CException (classe)](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)
