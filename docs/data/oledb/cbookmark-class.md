---
title: CBookmark, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: d3d82ea09b7ed2c1cbaf325906b4f9b480e1eb4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359337"
---
# <a name="cbookmark-class"></a>CBookmark, classe

Détient une valeur de signet dans son tampon.

## <a name="syntax"></a>Syntaxe

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
La taille du tampon de signet dans les octets. Lorsque *nSize* est nul, le tampon de signets sera créé dynamiquement au moment de l’exécution.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CBookmark (en)](#cbookmark)|Le constructeur|
|[GetBuffer](#getbuffer)|Récupère le pointeur vers le tampon.|
|[GetSize](#getsize)|Récupère la taille du tampon dans les octets.|
|[SetBookmark SetBookmark SetBookmark SetBook](#setbookmark)|Définit la valeur du signet.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur](#operator)|Assigne `CBookmark` une classe à une autre.|

## <a name="remarks"></a>Notes

`CBookmark<0>`est une spécialisation `CBookmark`de modèle de ; son tampon est créé dynamiquement au moment de l’exécution.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a>CBookmark::CBookmark

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
[dans] Taille du tampon de signet dans les octets.

### <a name="remarks"></a>Notes

La première fonction définit le tampon à NULL et la taille du tampon à 0. La deuxième fonction définit la taille du tampon à *nSize*, et le tampon à un tableau d’octet de *octets nSize.*

> [!NOTE]
> Cette fonction n’est disponible que dans `CBookmark<0>`.

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a>CBookmark::GetBuffer

Récupère le pointeur sur le tampon de signet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le tampon de signet.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a>CBookmark::GetSize

Récupère la taille du tampon de signet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Valeur de retour

Taille de la mémoire tampon en octets.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a>CBookmark::SetBookmark

Copie la valeur de signet référencée par *pBuffer* au `CBookmark` tampon et définit la taille du tampon à *nSize*.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
[dans] La taille du tampon de signet.

*pBuffer*<br/>
[dans] Un pointeur vers le tableau byte contenant la valeur de signet.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction n’est disponible que dans `CBookmark<0>`.

## <a name="cbookmarkoperator-"></a><a name="operator"></a>CBookmark::opérateur

Assigne `CBookmark` un objet à un autre.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Notes

Cet opérateur n’est nécessaire que dans `CBookmark<0>`.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB Consumer Templates Référence](../../data/oledb/ole-db-consumer-templates-reference.md)
