---
title: Classe CStrBufT
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
ms.openlocfilehash: 71d7b6f7d53e9613b1ac26013d73c1dbd1ef0aab
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746925"
---
# <a name="cstrbuft-class"></a>Classe CStrBufT

Cette classe fournit le `GetBuffer` nettoyage `ReleaseBuffer` automatique des `CStringT` ressources et fait appel à un objet existant.

## <a name="syntax"></a>Syntaxe

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Paramètres

*TCharType (TCharType)*<br/>
Le type de `CStrBufT` personnage de la classe. Il peut s'agir d'une des méthodes suivantes :

- **char** (pour les cordes de caractère ANSI)

- **wchar_t** (pour les chaînes de caractères Unicode)

- TCHAR (pour les chaînes de caractères ANSI et Unicode)

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|PCXSTR|Un pointeur à une chaîne constante.|
|PXSTR (en)|Un pointeur à une chaîne.|
|`StringType`|Le type de chaîne dont le tampon doit être manipulé par des spécialisations de ce modèle de classe.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Le constructeur de l’objet tampon de chaîne.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|Définit la longueur tampon de caractère de l’objet de chaîne associé.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CStrBufT::opérateur PCXSTR](#operator_pcxstr)|Récupère un pointeur **de cône** au tampon de caractère de l’objet de chaîne associé.|
|[CStrBufT::opérateur PXSTR](#operator_pxstr)|Récupère un pointeur sur le tampon de caractère de l’objet de chaîne associé.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|Déterminez automatiquement la nouvelle longueur de la chaîne à la libération.|
|[CStrBufT::SET_LENGTH](#set_length)|Réglez la longueur de l’objet de chaîne à l’heure GetBuffer|

## <a name="remarks"></a>Notes

Cette classe est utilisée comme une classe d’emballage pour remplacer les appels à [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), ou [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) et `ReleaseBuffer`.

Principalement conçu comme une classe `CStrBufT` d’aide, fournit un moyen pratique pour un développeur de travailler avec `ReleaseBuffer`le tampon de caractère d’un objet de chaîne sans se soucier de comment ou quand appeler . Cela est possible parce que l’objet d’emballage sort naturellement de portée dans le cas d’une exception ou de multiples voies de code sortantes; libérant la ressource de chaîne de son destructeur.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpstr.h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT::AUTO_LENGTH

Déterminez automatiquement la nouvelle longueur de la chaîne à la libération.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Notes

Déterminez automatiquement la nouvelle longueur de la chaîne à la libération. La corde doit être annulée.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

Construit un objet tampon.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
L’objet de chaîne associé au tampon. Typiquement, le développeur utilisera les composants dactylographiés prédéfinis `CStrBuf` de (variante `CStrBufA` TCHAR), (variante de**l’omble)** et `CStrBufW` (**wchar_t** variante).

*nMinLength (en)*<br/>
La longueur minimale du tampon de caractère.

*dwFlags*<br/>
Détermine si la longueur de la chaîne est automatiquement déterminée. Il peut s'agir d'une des méthodes suivantes :

- AUTO_LENGTH Longueur de chaîne est automatiquement déterminée lorsque [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) est appelé. La corde doit être annulée. Valeur par défaut.

- SET_LENGTH Longueur de chaîne est définie lorsque [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) est appelé.

### <a name="remarks"></a>Notes

Crée un tampon de chaîne pour l’objet de chaîne associé. Pendant la construction, [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) ou [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) est appelé.

Notez que le constructeur de copie est **privé**.

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT::opérateur PCXSTR

Accéde directement aux caractères stockés dans l’objet à chaîne associé sous forme de chaîne de style C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de caractère aux données de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur au tampon de caractère d’un objet de chaîne. Le contenu de l’objet de chaîne ne peut pas être changé avec ce pointeur.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT::opérateur PXSTR

Accéde directement aux caractères stockés dans l’objet à chaîne associé sous forme de chaîne de style C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de caractère aux données de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur au tampon de caractère d’un objet de chaîne. Le développeur peut modifier le contenu de l’objet de chaîne avec ce pointeur.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::PCXSTR

Un pointeur à une chaîne constante.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::PXSTR

Un pointeur à une chaîne.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT::SET_LENGTH

Réglez la longueur `GetBuffer` de l’objet de chaîne à la fois.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Notes

Réglez la longueur de l’objet de chaîne au moment de GetBuffer.

Détermine si [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) sont appelés lorsque l’objet tampon de chaîne est construit.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT::SetLength

Définit la longueur du tampon de caractère.

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>Paramètres

*nLength (en)*<br/>
La nouvelle longueur du tampon de caractère de l’objet de chaîne.

> [!NOTE]
> Doit être inférieur ou égal à la longueur minimale `CStrBufT`du tampon spécifié dans le constructeur de .

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir la longueur de la chaîne représentée par l’objet tampon.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::StringType

Le type de chaîne dont le tampon doit être manipulé par des spécialisations de ce modèle de classe.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Notes

`TCharType`est le type de personnage utilisé pour spécialiser le modèle de classe.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
