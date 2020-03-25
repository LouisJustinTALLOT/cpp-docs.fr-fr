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
ms.openlocfilehash: e15be3342b32b432c438b65ec57765cb135f5316
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212236"
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
Taille de la mémoire tampon du signet, en octets. Lorsque *nSize* est égal à zéro, la mémoire tampon du signet est créée dynamiquement au moment de l’exécution.

## <a name="requirements"></a>Spécifications

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
|[opérateur =](#operator)|Assigne une classe `CBookmark` à une autre.|

## <a name="remarks"></a>Notes

`CBookmark<0>` est une spécialisation de modèle de `CBookmark`; sa mémoire tampon est créée dynamiquement au moment de l’exécution.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a>CBookmark :: CBookmark

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Paramètres

*nSize*<br/>
dans Taille de la mémoire tampon du signet, en octets.

### <a name="remarks"></a>Notes

La première fonction affecte la valeur NULL à la mémoire tampon et la taille de la mémoire tampon à 0. La deuxième fonction définit la taille de la mémoire tampon sur *nSize*et la mémoire tampon sur un tableau d’octets *nSize* octets.

> [!NOTE]
>  Cette fonction est uniquement disponible dans `CBookmark<0>`.

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a>CBookmark :: GetBuffer

Récupère le pointeur vers la mémoire tampon de signet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la mémoire tampon de signet.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a>CBookmark :: dela

Récupère la taille de la mémoire tampon du signet.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Valeur de retour

Taille de la mémoire tampon en octets.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a>CBookmark :: SetBookmark

Copie la valeur de signet référencée par *pbuffer* dans la mémoire tampon de `CBookmark` et définit la taille de la mémoire tampon sur *nSize*.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Paramètres

*nSize*<br/>
dans Taille de la mémoire tampon du signet.

*pBuffer*<br/>
dans Pointeur vers le tableau d’octets contenant la valeur de signet.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est uniquement disponible dans `CBookmark<0>`.

## <a name="cbookmarkoperator-"></a><a name="operator"></a>CBookmark :: Operator =

Assigne un objet `CBookmark` à un autre.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Notes

Cet opérateur est nécessaire uniquement dans `CBookmark<0>`.

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
