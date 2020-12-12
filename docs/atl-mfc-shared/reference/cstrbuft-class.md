---
description: 'En savoir plus sur : classe CStrBufT'
title: CStrBufT, classe
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 4cc38f13d740b7def65c6f958d53af7b367adcb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166614"
---
# <a name="cstrbuft-class"></a>CStrBufT, classe

Cette classe fournit un nettoyage automatique des ressources pour `GetBuffer` et `ReleaseBuffer` appelle sur un `CStringT` objet existant.

## <a name="syntax"></a>Syntaxe

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Paramètres

*TCharType*<br/>
Type de caractère de la `CStrBufT` classe. Il peut s'agir d'une des méthodes suivantes :

- **`char`** (pour les chaînes de caractères ANSI)

- **`wchar_t`** (pour les chaînes de caractères Unicode)

- TCHAR (pour les chaînes de caractères ANSI et Unicode)

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|PCXSTR|Pointeur vers une chaîne constante.|
|PXSTR|Pointeur vers une chaîne.|
|`StringType`|Type de chaîne dont la mémoire tampon doit être manipulée par les spécialisations de ce modèle de classe.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Constructeur de l’objet de mémoire tampon de chaîne.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStrBufT :: SetLength](#setlength)|Définit la longueur de la mémoire tampon de caractères de l’objet String associé.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CStrBufT :: Operator PCXSTR](#operator_pcxstr)|Récupère un **`const`** pointeur vers la mémoire tampon de caractères de l’objet String associé.|
|[CStrBufT :: Operator PXSTR](#operator_pxstr)|Récupère un pointeur vers la mémoire tampon de caractères de l’objet String associé.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[CStrBufT :: AUTO_LENGTH](#auto_length)|Détermine automatiquement la nouvelle longueur de la chaîne au niveau de la mise en sortie.|
|[CStrBufT :: SET_LENGTH](#set_length)|Définir la longueur de l’objet String à l’heure GetBuffer|

## <a name="remarks"></a>Notes

Cette classe est utilisée comme classe wrapper pour remplacer les appels à [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), ou [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) et `ReleaseBuffer` .

Conçu principalement comme une classe d’assistance, `CStrBufT` offre un moyen pratique pour un développeur de travailler avec la mémoire tampon de caractères d’un objet String sans se soucier de savoir comment ou quand appeler `ReleaseBuffer` . Cela est possible parce que l’objet wrapper est hors de portée naturellement dans le cas d’une exception ou de plusieurs chemins de code de sortie. force son destructeur à libérer la ressource de chaîne.

## <a name="requirements"></a>Spécifications

**En-tête :** atlsimpstr. h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a> CStrBufT :: AUTO_LENGTH

Détermine automatiquement la nouvelle longueur de la chaîne au niveau de la mise en sortie.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Notes

Détermine automatiquement la nouvelle longueur de la chaîne au niveau de la mise en sortie. La chaîne doit se terminer par un caractère null.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a> CStrBufT::CStrBufT

Construit un objet de mémoire tampon.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Objet String associé à la mémoire tampon. En règle générale, le développeur utilise les typedefs prédéfinis de `CStrBuf` (variante TCHAR), `CStrBufA` ( **`char`** Variant) et `CStrBufW` ( **`wchar_t`** Variant).

*nMinLength*<br/>
Longueur minimale de la mémoire tampon de caractères.

*dwFlags*<br/>
Détermine si la longueur de chaîne est déterminée automatiquement. Il peut s'agir d'une des méthodes suivantes :

- AUTO_LENGTH longueur de chaîne est déterminée automatiquement quand [CSimpleStringT :: Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) est appelé. La chaîne doit se terminer par un caractère null. Valeur par défaut.

- SET_LENGTH longueur de chaîne est définie lors de l’appel de [CSimpleStringT :: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) .

### <a name="remarks"></a>Notes

Crée une mémoire tampon de chaîne pour l’objet String associé. Pendant la construction, [CSimpleStringT :: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) ou [CSimpleStringT :: GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) est appelé.

Notez que le constructeur de copie est **`private`** .

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a> CStrBufT :: Operator PCXSTR

Accède directement aux caractères stockés dans l’objet String associé en tant que chaîne de style C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur de caractère vers les données de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur vers la mémoire tampon de caractères d’un objet String. Le contenu de l’objet String ne peut pas être modifié à l’aide de ce pointeur.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a> CStrBufT :: Operator PXSTR

Accède directement aux caractères stockés dans l’objet String associé en tant que chaîne de style C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur de caractère vers les données de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur vers la mémoire tampon de caractères d’un objet String. Le développeur peut modifier le contenu de l’objet String avec ce pointeur.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a> CStrBufT ::P CXSTR

Pointeur vers une chaîne constante.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a> CStrBufT ::P XSTR

Pointeur vers une chaîne.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a> CStrBufT :: SET_LENGTH

Définissez la longueur de l’objet String dans le `GetBuffer` temps.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Notes

Définissez la longueur de l’objet String à l’heure GetBuffer.

Détermine si [CSimpleStringT :: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [CSimpleStringT :: GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) sont appelés lors de la construction de l’objet de mémoire tampon de chaîne.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a> CStrBufT :: SetLength

Définit la longueur de la mémoire tampon de caractères.

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>Paramètres

*nLength*<br/>
Nouvelle longueur de la mémoire tampon de caractères de l’objet String.

> [!NOTE]
> Doit être inférieure ou égale à la longueur de mémoire tampon minimale spécifiée dans le constructeur de `CStrBufT` .

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir la longueur de la chaîne représentée par l’objet de mémoire tampon.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a> CStrBufT::StringType

Type de chaîne dont la mémoire tampon doit être manipulée par les spécialisations de ce modèle de classe.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Notes

`TCharType` type de caractère utilisé pour spécialiser le modèle de classe.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
