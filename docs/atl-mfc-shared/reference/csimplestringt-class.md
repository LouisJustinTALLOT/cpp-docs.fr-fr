---
description: 'En savoir plus sur : classe CSimpleStringT'
title: CSimpleStringT, classe
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: fd2ddf79e94827ad42411eeec71dde2fce28bd8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166653"
---
# <a name="csimplestringt-class"></a>CSimpleStringT, classe

Cette classe représente un `CSimpleStringT` objet.

## <a name="syntax"></a>Syntaxe

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Paramètres

*BaseType*<br/>
Type de caractère de la classe String. Il peut s'agir d'une des méthodes suivantes :

- **`char`** (pour les chaînes de caractères ANSI).

- **`wchar_t`** (pour les chaînes de caractères Unicode).

- TCHAR (pour les chaînes de caractères ANSI et Unicode).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT ::P CXSTR](#pcxstr)|Pointeur vers une chaîne constante.|
|[CSimpleStringT ::P XSTR](#pxstr)|Pointeur vers une chaîne.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Construit `CSimpleStringT` des objets de différentes façons.|
|[CSimpleStringT :: ~ CSimpleStringT](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT :: Append](#append)|Ajoute un `CSimpleStringT` objet à un objet existant `CSimpleStringT` .|
|[CSimpleStringT::AppendChar](#appendchar)|Ajoute un caractère à un objet existant `CSimpleStringT` .|
|[CSimpleStringT::CopyChars](#copychars)|Copie un ou des caractères dans une autre chaîne.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Copie un ou des caractères dans une autre chaîne dans laquelle les mémoires tampons se chevauchent.|
|[CSimpleStringT :: Empty](#empty)|Force une chaîne à avoir une longueur de zéro.|
|[CSimpleStringT::FreeExtra](#freeextra)|Libère toute mémoire supplémentaire précédemment allouée par l’objet String.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Récupère la longueur allouée d’un `CSimpleStringT` objet.|
|[CSimpleStringT :: GetAt](#getat)|Retourne le caractère à une position donnée.|
|[CSimpleStringT :: GetBuffer](#getbuffer)|Retourne un pointeur vers les caractères d’un `CSimpleStringT` .|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Retourne un pointeur vers les caractères d’un `CSimpleStringT` , en tronquant la longueur spécifiée.|
|[CSimpleStringT :: GetLength](#getlength)|Retourne le nombre de caractères dans un `CSimpleStringT` objet.|
|[CSimpleStringT::GetManager](#getmanager)|Récupère le gestionnaire de mémoire de l' `CSimpleStringT` objet.|
|[CSimpleStringT :: GetString](#getstring)|Récupère la chaîne de caractères|
|[CSimpleStringT :: IsEmpty](#isempty)|Teste si un `CSimpleStringT` objet ne contient aucun caractère.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Désactive le décompte de références et protège la chaîne dans la mémoire tampon.|
|[CSimpleStringT ::P réalloué](#preallocate)|Alloue une quantité de mémoire spécifique pour la mémoire tampon de caractères.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Libère le contrôle de la mémoire tampon retournée par `GetBuffer` .|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Libère le contrôle de la mémoire tampon retournée par `GetBuffer` .|
|[CSimpleStringT :: SetAt](#setat)|Définit un caractère à une position donnée.|
|[CSimpleStringT::SetManager](#setmanager)|Définit le gestionnaire de mémoire d’un `CSimpleStringT` objet.|
|[CSimpleStringT :: SetString](#setstring)|Définit la chaîne d’un `CSimpleStringT` objet.|
|[CSimpleStringT :: StringLength](#stringlength)|Retourne le nombre de caractères de la chaîne spécifiée.|
|[CSimpleStringT :: TRUNCATE](#truncate)|Tronque la chaîne à une longueur spécifiée.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Active le décompte de références et libère la chaîne dans la mémoire tampon.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT :: Operator PCXSTR](#operator_pcxstr)|Accède directement aux caractères stockés dans un `CSimpleStringT` objet sous la forme d’une chaîne de style C.|
|[CSimpleStringT::operator\[\]](#operator_at)|Retourne le caractère à une position donnée, à savoir la substitution d’opérateur pour `GetAt` .|
|[CSimpleStringT :: Operator + =](#operator_add_eq)|Concatène une nouvelle chaîne à la fin d’une chaîne existante.|
|[CSimpleStringT :: Operator =](#operator_eq)|Assigne une nouvelle valeur à un `CSimpleStringT` objet.|

### <a name="remarks"></a>Notes

`CSimpleStringT` est la classe de base pour les différentes classes de chaîne prises en charge par Visual C++. Il offre une prise en charge minimale de la gestion de la mémoire de l’objet String et de la manipulation de mémoire tampon de base. Pour obtenir des objets String plus avancés, consultez la [classe CStringT](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlsimpstr. h

## <a name="csimplestringtappend"></a><a name="append"></a> CSimpleStringT :: Append

Ajoute un `CSimpleStringT` objet à un objet existant `CSimpleStringT` .

### <a name="syntax"></a>Syntaxe

```cpp
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Paramètres

*strSrc*<br/>
`CSimpleStringT`Objet à ajouter.

*pszSrc*<br/>
Pointeur vers une chaîne contenant les caractères à ajouter.

*nLength*<br/>
Nombre de caractères à ajouter.

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajouter un `CSimpleStringT` objet existant à un autre `CSimpleStringT` objet.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a> CSimpleStringT::AppendChar

Ajoute un caractère à un objet existant `CSimpleStringT` .

### <a name="syntax"></a>Syntaxe

```cpp
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Paramètres

*cascade*<br/>
Caractère à ajouter

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter le caractère spécifié à la fin d’un `CSimpleStringT` objet existant.

## <a name="csimplestringtcopychars"></a><a name="copychars"></a> CSimpleStringT::CopyChars

Copie un ou des caractères dans un `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Paramètres

*pchDest*<br/>
Pointeur vers une chaîne de caractères.

*pchSrc*<br/>
Pointeur vers une chaîne contenant les caractères à copier.

*nChars*<br/>
Nombre de caractères *pchSrc* à copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier les caractères de *pchSrc* dans la chaîne *pchDest* .

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a> CSimpleStringT::CopyCharsOverlapped

Copie un ou des caractères dans un `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Paramètres

*pchDest*<br/>
Pointeur vers une chaîne de caractères.

*pchSrc*<br/>
Pointeur vers une chaîne contenant les caractères à copier.

*nChars*<br/>
Nombre de caractères *pchSrc* à copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier les caractères de *pchSrc* dans la chaîne *pchDest* . Contrairement `CopyChars` `CopyCharsOverlapped` à, fournit une méthode sécurisée pour la copie à partir de mémoires tampons de caractères qui peuvent être superposées.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CSimpleStringT :: CopyChars](#copychars)ou le code source pour `CSimpleStringT::SetString` (situé dans atlsimpstr. h).

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a> CSimpleStringT::CSimpleStringT

Construit un objet `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Paramètres

*strSrc*<br/>
Objet existant `CSimpleStringT` à copier dans cet `CSimpleStringT` objet.

*pchSrc*<br/>
Pointeur vers un tableau de caractères de longueur *nLength*, non null terminé.

*pszSrc*<br/>
Chaîne terminée par le caractère null à copier dans cet `CSimpleStringT` objet.

*nLength*<br/>
Nombre de caractères dans `pch` .

*pStringMgr*<br/>
Pointeur vers le gestionnaire de mémoire de l' `CSimpleStringT` objet. Pour plus d’informations sur et sur la `IAtlStringMgr` gestion de la mémoire pour `CSimpleStringT` , consultez Gestion de la [mémoire et CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Notes

Construisez un nouvel `CSimpleStringT` objet. Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, des exceptions de mémoire peuvent se produire.

### <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de `CSimpleStringT::CSimpleStringT` à l’aide de la bibliothèque ATL **`typedef`** `CSimpleString` . `CSimpleString` est une spécialisation couramment utilisée du modèle de classe `CSimpleStringT` .

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

## <a name="csimplestringtempty"></a><a name="empty"></a> CSimpleStringT :: Empty

Convertit cet `CSimpleStringT` objet en chaîne vide et libère la mémoire en fonction des besoins.

### <a name="syntax"></a>Syntaxe

```cpp
void Empty() throw();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Strings : nettoyage des exceptions CString](../cstring-exception-cleanup.md).

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a> CSimpleStringT::FreeExtra

Libère toute mémoire supplémentaire précédemment allouée par la chaîne, mais qui n’est plus nécessaire.

### <a name="syntax"></a>Syntaxe

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Notes

Cela doit réduire la surcharge de mémoire consommée par l’objet String. La méthode réaffecte la mémoire tampon à la longueur exacte retournée par [GetLength](#getlength).

### <a name="example"></a>Exemple

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>Notes

La sortie de cet exemple est la suivante :

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a> CSimpleStringT::GetAllocLength

Récupère la longueur allouée d’un `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Nombre de caractères alloués pour cet objet.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer le nombre de caractères alloués pour cet `CSimpleStringT` objet. Pour obtenir un exemple d’appel de cette fonction, consultez [FreeExtra](#freeextra) .

## <a name="csimplestringtgetat"></a><a name="getat"></a> CSimpleStringT :: GetAt

Retourne un caractère à partir d’un `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Paramètres

*iChar*<br/>
Index de base zéro du caractère dans l' `CSimpleStringT` objet. Le paramètre *iChar* doit être supérieur ou égal à 0 et inférieur à la valeur retournée par [GetLength](#getlength). Sinon, `GetAt` génère une exception.

### <a name="return-value"></a>Valeur renvoyée

`XCHAR`Qui contient le caractère à la position spécifiée dans la chaîne.

### <a name="remarks"></a>Notes

Appelez cette méthode pour retourner le caractère unique spécifié par *iChar*. L’opérateur d’indice surchargé (**[]**) est un alias pratique pour `GetAt` . La marque de fin null est adressable sans générer d’exception à l’aide de `GetAt` . Toutefois, il n’est pas compté par `GetLength` et la valeur retournée est 0.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `CSimpleStringT::GetAt` .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a> CSimpleStringT :: GetBuffer

Retourne un pointeur vers la mémoire tampon de caractères interne de l' `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Paramètres

*nMinBufferLength*<br/>
Nombre minimal de caractères que la mémoire tampon de caractères peut contenir. Cette valeur n’inclut pas d’espace pour une marque de fin null.

Si la valeur de *nMinBufferLength* est supérieure à la longueur de la mémoire tampon actuelle, `GetBuffer` détruit la mémoire tampon actuelle, la remplace par une mémoire tampon de la taille demandée et réinitialise le nombre de références de l’objet à zéro. Si vous avez précédemment appelé [LockBuffer](#lockbuffer) sur cette mémoire tampon, vous perdez le verrouillage de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

`PXSTR`Pointeur vers la mémoire tampon de caractères (se terminant par null) de l’objet.

### <a name="remarks"></a>Notes

Appelez cette méthode pour retourner le contenu de la mémoire tampon de l' `CSimpleStringT` objet. Le retourné `PXSTR` n’est pas une constante et, par conséquent, permet une modification directe du `CSimpleStringT` contenu.

Si vous utilisez le pointeur retourné par `GetBuffer` pour modifier le contenu de la chaîne, vous devez appeler [ReleaseBuffer](#releasebuffer) avant d’utiliser d’autres `CSimpleStringT` méthodes membres.

L’adresse retournée par `GetBuffer` peut ne pas être valide après l’appel à `ReleaseBuffer` , car des `CSimpleStringT` opérations supplémentaires peuvent entraîner la `CSimpleStringT` réallocation de la mémoire tampon. La mémoire tampon n’est pas réallouée si vous ne modifiez pas la longueur de `CSimpleStringT` .

La mémoire tampon est automatiquement libérée lorsque l' `CSimpleStringT` objet est détruit.

Si vous assurez le suivi de la longueur de chaîne vous-même, vous ne devez pas ajouter le caractère null de fin. Toutefois, vous devez spécifier la longueur de chaîne finale lorsque vous publiez la mémoire tampon avec `ReleaseBuffer` . Si vous ajoutez un caractère null de fin, vous devez passer-1 (valeur par défaut) pour la longueur. `ReleaseBuffer` détermine ensuite la longueur de la mémoire tampon.

Si la mémoire est insuffisante pour satisfaire la `GetBuffer` demande, cette méthode lève une CMemoryException *.

### <a name="example"></a>Exemple

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a> CSimpleStringT::GetBufferSetLength

Retourne un pointeur vers la mémoire tampon de caractères interne de l' `CSimpleStringT` objet, en tronquant ou en augmentant sa longueur si nécessaire pour correspondre exactement à la longueur spécifiée dans *nLength*.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Paramètres

*nLength*<br/>
Taille exacte de la `CSimpleStringT` mémoire tampon de caractères en caractères.

### <a name="return-value"></a>Valeur renvoyée

`PXSTR`Pointeur vers la mémoire tampon de caractères (se terminant par null) de l’objet.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer une longueur spécifiée de la mémoire tampon interne de l' `CSimpleStringT` objet. Le `PXSTR` pointeur retourné n’est pas **`const`** et permet donc une modification directe du `CSimpleStringT` contenu.

Si vous utilisez le pointeur retourné par [GetBufferSetLength](#getbuffersetlength) pour modifier le contenu de la chaîne, appelez `ReleaseBuffer` pour mettre à jour l’état interne de `CsimpleStringT` avant d’utiliser d’autres `CSimpleStringT` méthodes.

L’adresse retournée par `GetBufferSetLength` peut ne pas être valide après l’appel à `ReleaseBuffer` , car des `CSimpleStringT` opérations supplémentaires peuvent entraîner la `CSimpleStringT` réallocation de la mémoire tampon. La mémoire tampon n’est pas réassignée si vous ne modifiez pas la longueur de `CSimpleStringT` .

La mémoire tampon est automatiquement libérée lorsque l' `CSimpleStringT` objet est détruit.

Si vous assurez le suivi de la longueur de chaîne vous-même, n’ajoutez pas le caractère null de fin. Vous devez spécifier la longueur de chaîne finale lorsque vous libérez la mémoire tampon à l’aide de `ReleaseBuffer` . Si vous ajoutez un caractère null de fin lorsque vous appelez `ReleaseBuffer` , pass-1 (valeur par défaut) pour la longueur à `ReleaseBuffer` , et `ReleaseBuffer` exécute un `strlen` sur la mémoire tampon pour déterminer sa longueur.

Pour plus d’informations sur le décompte de références, consultez les articles suivants :

- [Gestion des durées de vie des objets par le biais du décompte de références](/windows/win32/com/managing-object-lifetimes-through-reference-counting) dans la SDK Windows.

- [Implémentation du décompte de références](/windows/win32/com/implementing-reference-counting) dans la SDK Windows.

- [Règles de gestion des décomptes de références](/windows/win32/com/rules-for-managing-reference-counts) dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::GetBufferSetLength`.

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

## <a name="csimplestringtgetlength"></a><a name="getlength"></a> CSimpleStringT :: GetLength

Retourne le nombre de caractères dans l' `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
int GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Nombre de caractères dans la chaîne.

### <a name="remarks"></a>Notes

Appelez cette méthode pour retourner le nombre de caractères dans l’objet. Le nombre n’inclut pas de marque de fin null.

Pour les jeux de caractères multioctets (MBCS), `GetLength` compte chaque caractère 8 bits ; autrement dit, un octet de tête et de fin dans un caractère multioctet est compté comme deux octets. Pour obtenir un exemple d’appel de cette fonction, consultez [FreeExtra](#freeextra) .

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a> CSimpleStringT::GetManager

Récupère le gestionnaire de mémoire de l' `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le gestionnaire de mémoire de l' `CSimpleStringT` objet.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le gestionnaire de mémoire utilisé par l' `CSimpleStringT` objet. Pour plus d’informations sur les gestionnaires de mémoire et les objets String, consultez Gestion de la [mémoire et CStringT](../memory-management-with-cstringt.md).

## <a name="csimplestringtgetstring"></a><a name="getstring"></a> CSimpleStringT :: GetString

Récupère la chaîne de caractères.

### <a name="syntax"></a>Syntaxe

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une chaîne de caractères se terminant par null.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer la chaîne de caractères associée à l' `CSimpleStringT` objet.

> [!NOTE]
> Le `PCXSTR` pointeur retourné a la **`const`** valeur et n’autorise pas la modification directe du `CSimpleStringT` contenu.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a> CSimpleStringT :: IsEmpty

Teste un `CSimpleStringT` objet pour la condition vide.

### <a name="syntax"></a>Syntaxe

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l' `CSimpleStringT` objet a une longueur de 0 ; sinon, false.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer si l’objet contient une chaîne vide.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a> CSimpleStringT::LockBuffer

Désactive le décompte de références et protège la chaîne dans la mémoire tampon.

### <a name="syntax"></a>Syntaxe

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CSimpleStringT` objet ou une chaîne terminée par le caractère null.

### <a name="remarks"></a>Notes

Appelez cette méthode pour verrouiller la mémoire tampon de l' `CSimpleStringT` objet. En appelant `LockBuffer` , vous créez une copie de la chaîne, avec la valeur-1 pour le décompte de références. Lorsque la valeur du nombre de références est-1, la chaîne dans la mémoire tampon est considérée comme étant à l’état « verrouillé ». Bien qu’en état verrouillé, la chaîne est protégée de deux manières :

- Aucune autre chaîne ne peut obtenir une référence aux données dans la chaîne verrouillée, même si cette chaîne est assignée à la chaîne verrouillée.

- La chaîne verrouillée ne fait jamais référence à une autre chaîne, même si cette autre chaîne est copiée dans la chaîne verrouillée.

En verrouillant la chaîne dans la mémoire tampon, vous vous assurez que la conservation exclusive de la chaîne dans la mémoire tampon reste intacte.

Une fois que vous avez terminé avec `LockBuffer` , appelez [UnlockBuffer](#unlockbuffer) pour réinitialiser le décompte de références à 1.

> [!NOTE]
> Si vous appelez [GetBuffer](#getbuffer) sur une mémoire tampon verrouillée et que vous définissez le `GetBuffer` paramètre sur une valeur supérieure à `nMinBufferLength` la longueur de la mémoire tampon actuelle, vous perdez le verrouillage de la mémoire tampon. Ce type d’appel permet de `GetBuffer` détruire la mémoire tampon en cours, de la remplacer par une mémoire tampon de la taille demandée et de réinitialiser le décompte de références à zéro.

Pour plus d’informations sur le décompte de références, consultez les articles suivants :

- [Gestion des durées de vie des objets par le biais du décompte de références](/windows/win32/com/managing-object-lifetimes-through-reference-counting) dans le SDK Windows

- [Implémentation du décompte de références](/windows/win32/com/implementing-reference-counting) dans le SDK Windows

- [Règles de gestion des décomptes de références](/windows/win32/com/rules-for-managing-reference-counts) dans le SDK Windows

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

## <a name="csimplestringtoperator"></a><a name="operator_at"></a> CSimpleStringT ::, opérateur\[\]

Appelez cette fonction pour accéder à un caractère unique du tableau de caractères.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Paramètres

*iChar*<br/>
Index de base zéro d’un caractère dans la chaîne.

### <a name="remarks"></a>Notes

L’opérateur d’indice surchargé (**[]**) retourne un caractère unique spécifié par l’index de base zéro dans *iChar*. Cet opérateur est un substitut pratique de la fonction membre [GetAt](#getat) .

> [!NOTE]
> Vous pouvez utiliser l’opérateur d’indice (**[]**) pour obtenir la valeur d’un caractère dans un `CSimpleStringT` , mais vous ne pouvez pas l’utiliser pour modifier la valeur d’un caractère dans un `CSimpleStringT` .

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a> CSimpleStringT ::, opérateur \[\]

Appelez cette fonction pour accéder à un caractère unique du tableau de caractères.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Paramètres

*iChar*<br/>
Index de base zéro d’un caractère dans la chaîne.

### <a name="remarks"></a>Notes

L’opérateur d’indice surchargé (**[]**) retourne un caractère unique spécifié par l’index de base zéro dans *iChar*. Cet opérateur est un substitut pratique de la fonction membre [GetAt](#getat) .

> [!NOTE]
> Vous pouvez utiliser l’opérateur d’indice (**[]**) pour obtenir la valeur d’un caractère dans un `CSimpleStringT` , mais vous ne pouvez pas l’utiliser pour modifier la valeur d’un caractère dans un `CSimpleStringT` .

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a> CSimpleStringT :: Operator + =

Joint une nouvelle chaîne ou un caractère à la fin d’une chaîne existante.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>Paramètres

*pszSrc*<br/>
Pointeur vers une chaîne se terminant par null.

*strSrc*<br/>
Pointeur vers un objet existant `CSimpleStringT` .

*cascade*<br/>
Caractère à ajouter.

### <a name="remarks"></a>Notes

L’opérateur accepte un autre `CSimpleStringT` objet ou un caractère. Notez que des exceptions de mémoire peuvent se produire chaque fois que vous utilisez cet opérateur de concaténation, car un nouveau stockage peut être alloué pour les caractères ajoutés à cet `CSimpleStringT` objet.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a> CSimpleStringT :: Operator =

Assigne une nouvelle valeur à un `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Paramètres

*pszSrc*<br/>
Pointeur vers une chaîne se terminant par null.

*strSrc*<br/>
Pointeur vers un objet existant `CSimpleStringT` .

### <a name="remarks"></a>Notes

Si la chaîne de destination (côté gauche) est déjà suffisamment grande pour stocker les nouvelles données, aucune nouvelle allocation de mémoire n’est effectuée. Notez que des exceptions de mémoire peuvent se produire chaque fois que vous utilisez l’opérateur d’assignation, car un nouveau stockage est souvent alloué pour contenir l' `CSimpleStringT` objet résultant.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::operator =`.

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a> CSimpleStringT :: Operator PCXSTR

Accède directement aux caractères stockés dans un `CSimpleStringT` objet sous la forme d’une chaîne de style C.

### <a name="syntax"></a>Syntaxe

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Pointeur de caractère vers les données de la chaîne.

### <a name="remarks"></a>Notes

Aucun caractère n’est copié ; seul un pointeur est retourné. Soyez vigilant avec cet opérateur. Si vous modifiez un `CString` objet après avoir obtenu le pointeur de caractère, vous risquez de provoquer une réallocation de mémoire qui invalide le pointeur.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::operator PCXSTR`.

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a> CSimpleStringT ::P CXSTR

Pointeur vers une chaîne constante.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a> CSimpleStringT ::P réalloué

Alloue une quantité spécifique d’octets pour l' `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```cpp
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Paramètres

*nLength*<br/>
Taille exacte de la `CSimpleStringT` mémoire tampon de caractères en caractères.

### <a name="remarks"></a>Notes

Appelez cette méthode pour allouer une taille de mémoire tampon spécifique pour l' `CSimpleStringT` objet.

`CSimpleStringT` génère une exception STATUS_NO_MEMORY s’il ne parvient pas à allouer de l’espace pour la mémoire tampon de caractères. Par défaut, l’allocation de mémoire est effectuée par les fonctions de l’API WIN32 `HeapAlloc` ou `HeapReAlloc` .

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a> CSimpleStringT ::P XSTR

Pointeur vers une chaîne.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a> CSimpleStringT::ReleaseBuffer

Libère le contrôle de la mémoire tampon allouée par [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntaxe

```cpp
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Paramètres

*nNewLength*<br/>
Nouvelle longueur de la chaîne en caractères, sans compter une marque de fin null. Si la chaîne se termine par une valeur null, la valeur par défaut-1 définit la `CSimpleStringT` taille sur la longueur actuelle de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette méthode pour réallouer ou libérer la mémoire tampon de l’objet String. Si vous savez que la chaîne de la mémoire tampon se termine par une valeur null, vous pouvez omettre l’argument *nNewLength* . Si votre chaîne ne se termine pas par une valeur null, utilisez *nNewLength* pour spécifier sa longueur. L’adresse retournée par [GetBuffer](#getbuffer) n’est pas valide après l’appel à `ReleaseBuffer` ou toute autre `CSimpleStringT` opération.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::ReleaseBuffer`.

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a> CSimpleStringT::ReleaseBufferSetLength

Libère le contrôle de la mémoire tampon allouée par [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntaxe

```cpp
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Paramètres

*nNewLength*<br/>
Longueur de la chaîne en cours de libération

### <a name="remarks"></a>Notes

Cette fonction est fonctionnellement similaire à [ReleaseBuffer](#releasebuffer) , à ceci près qu’une longueur valide pour l’objet String doit être passée.

## <a name="csimplestringtsetat"></a><a name="setat"></a> CSimpleStringT :: SetAt

Définit un caractère unique à partir d’un `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```cpp
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Paramètres

*iChar*<br/>
Index de base zéro du caractère dans l' `CSimpleStringT` objet. Le paramètre *iChar* doit être supérieur ou égal à 0 et inférieur à la valeur retournée par [GetLength](#getlength).

*cascade*<br/>
Nouveau caractère.

### <a name="remarks"></a>Notes

Appelez cette méthode pour remplacer le caractère situé dans *iChar*. Cette méthode n’agrandit pas la chaîne si *iChar* dépasse les limites de la chaîne existante.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a> CSimpleStringT::SetManager

Spécifie le gestionnaire de mémoire de l' `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```cpp
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Paramètres

*pStringMgr*<br/>
Pointeur vers le nouveau gestionnaire de mémoire.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier un nouveau gestionnaire de mémoire utilisé par l' `CSimpleStringT` objet. Pour plus d’informations sur les gestionnaires de mémoire et les objets String, consultez Gestion de la [mémoire et CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a> CSimpleStringT :: SetString

Définit la chaîne d’un `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```cpp
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Paramètres

*pszSrc*<br/>
Pointeur vers une chaîne se terminant par null.

*nLength*<br/>
Nombre de caractères dans *pszSrc*.

### <a name="remarks"></a>Notes

Copiez une chaîne dans l' `CSimpleStringT` objet. `SetString` remplace les anciennes données de chaîne dans la mémoire tampon.

Les deux versions de `SetString` vérifient si *pszSrc* est un pointeur null, et si c’est le cas, levez une erreur E_INVALIDARG.

La version à un paramètre de `SetString` attend que *pszSrc* pointe vers une chaîne terminée par le caractère null.

La version à deux paramètres `SetString` s’attend également à ce que *pszSrc* soit une chaîne se terminant par un caractère null. Elle utilise *nLength* comme longueur de chaîne, sauf si elle rencontre d’abord un terminateur null.

La version à deux paramètres de `SetString` vérifie également si *pszSrc* pointe vers un emplacement dans la mémoire tampon actuelle dans `CSimpleStringT` . Dans ce cas particulier, `SetString` utilise une fonction de copie de mémoire qui ne remplace pas les données de chaîne au fur et à mesure de la copie des données de chaîne dans sa mémoire tampon.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a> CSimpleStringT :: StringLength

Retourne le nombre de caractères de la chaîne spécifiée.

### <a name="syntax"></a>Syntaxe

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Paramètres

*psz*<br/>
Pointeur vers une chaîne se terminant par null.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères dans *PSZ*; ne compte pas d’indicateur de fin null.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre de caractères de la chaîne pointée par *PSZ*.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a> CSimpleStringT :: TRUNCATE

Tronque la chaîne à la nouvelle longueur.

### <a name="syntax"></a>Syntaxe

```cpp
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Paramètres

*nNewLength*<br/>
Nouvelle longueur de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette méthode pour tronquer le contenu de la chaîne à la nouvelle longueur.

> [!NOTE]
> Cela n’affecte pas la longueur allouée de la mémoire tampon. Pour réduire ou augmenter la mémoire tampon actuelle, consultez [FreeExtra](#freeextra) et [allocate](#preallocate).

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::Truncate`.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a> CSimpleStringT::UnlockBuffer

Déverrouille la mémoire tampon de l' `CSimpleStringT` objet.

### <a name="syntax"></a>Syntaxe

```cpp
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour réinitialiser le décompte de références de la chaîne à 1.

Le `CSimpleStringT` destructeur appelle automatiquement `UnlockBuffer` pour s’assurer que la mémoire tampon n’est pas verrouillée lorsque le destructeur est appelé. Pour obtenir un exemple de cette méthode, consultez [LockBuffer](#lockbuffer).

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a> CSimpleStringT :: ~ CSimpleStringT

Détruit un objet `CSimpleStringT` .

### <a name="syntax"></a>Syntaxe

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour détruire l' `CSimpleStringT` objet.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
