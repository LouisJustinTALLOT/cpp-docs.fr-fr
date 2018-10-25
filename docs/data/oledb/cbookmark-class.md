---
title: CBookmark, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aef24c5c55bc3a3250c483536d0a63f967608b20
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064329"
---
# <a name="cbookmark-class"></a>CBookmark, classe

Contient une valeur de signet dans sa mémoire tampon.

## <a name="syntax"></a>Syntaxe

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Paramètres

*nSize*<br/>
La taille de la mémoire tampon de signet en octets. Lorsque *nSize* est égal à zéro, la mémoire tampon de signet sera créée dynamiquement au moment de l’exécution.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CBookmark](#cbookmark)|Le constructeur|
|[GetBuffer](#getbuffer)|Récupère le pointeur vers la mémoire tampon.|
|[GetSize](#getsize)|Récupère la taille de la mémoire tampon en octets.|
|[SetBookmark](#setbookmark)|Définit la valeur du signet.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](#operator)|Assigne un `CBookmark` classe vers un autre.|

## <a name="remarks"></a>Notes

`CBookmark<0>` est une spécialisation de modèle de `CBookmark`; sa mémoire tampon est créé dynamiquement au moment de l’exécution.

## <a name="cbookmark"></a> CBookmark::CBookmark

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark();
 
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Paramètres

*nSize*<br/>
[in] Taille de la mémoire tampon de signet en octets.

### <a name="remarks"></a>Notes

La première fonction définit la mémoire tampon sur NULL et la taille de mémoire tampon à 0. La deuxième fonction définit la taille de mémoire tampon sur *nSize*et la mémoire tampon de tableau d’octets de *nSize* octets.

> [!NOTE]
>  Cette fonction est disponible uniquement dans `CBookmark<0>`.

## <a name="getbuffer"></a> CBookmark::GetBuffer

Récupère le pointeur vers la mémoire tampon de signet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la mémoire tampon de signet.

## <a name="getsize"></a> CBookmark::GetSize

Récupère la taille de la mémoire tampon de signet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Valeur de retour

Taille de la mémoire tampon en octets.

## <a name="setbookmark"></a> CBookmark::SetBookmark

Copie la valeur de signet référencée par *pBuffer* à la `CBookmark` mettre en mémoire tampon et définit la taille de mémoire tampon sur *nSize*.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Paramètres

*nSize*<br/>
[in] La taille de la mémoire tampon de signet.

*pBuffer*<br/>
[in] Pointeur vers le tableau d’octets contenant la valeur du signet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est disponible uniquement dans `CBookmark<0>`.

## <a name="operator"></a> CBookmark::operator =

Assigne un `CBookmark` objet vers un autre.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Notes

Cet opérateur est nécessaire uniquement dans `CBookmark<0>`.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)