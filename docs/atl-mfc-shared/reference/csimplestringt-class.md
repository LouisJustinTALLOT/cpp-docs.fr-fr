---
title: Classe CSimpleStringT
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
ms.openlocfilehash: dce33289699b9e7b7484d1feb6335476f93dee9b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317688"
---
# <a name="csimplestringt-class"></a>Classe CSimpleStringT

Cette classe `CSimpleStringT` représente un objet.

## <a name="syntax"></a>Syntaxe

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Paramètres

*BaseType*<br/>
Le type de personnage de la classe de cordes. Il peut s'agir d'une des méthodes suivantes :

- **char** (pour les cordes de caractère ANSI).

- **wchar_t** (pour les chaînes de caractères Unicode).

- TCHAR (pour les chaînes de caractères ANSI et Unicode).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Un pointeur à une chaîne constante.|
|[CSimpleStringT::PXSTR](#pxstr)|Un pointeur à une chaîne.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Construit `CSimpleStringT` des objets de différentes manières.|
|[CSimpleStringT: :CSimpleStringT](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT::Append](#append)|Annexe un `CSimpleStringT` objet à `CSimpleStringT` un objet existant.|
|[CSimpleStringT::AppendChar](#appendchar)|Annexe d’un personnage `CSimpleStringT` à un objet existant.|
|[CSimpleStringT::CopyChars](#copychars)|Copie d’un personnage ou d’un personnage à une autre chaîne.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Copie d’un personnage ou d’un personnage à une autre chaîne dans laquelle les tampons se chevauchent.|
|[CSimpleStringT::Vide](#empty)|Force une corde à avoir une longueur de zéro.|
|[CSimpleStringT::FreeExtra](#freeextra)|Libère toute mémoire supplémentaire précédemment allouée par l’objet à cordes.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Récupère la longueur allouée `CSimpleStringT` d’un objet.|
|[CSimpleStringT::GetAt](#getat)|Retourne le personnage à une position donnée.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Retourne un pointeur aux `CSimpleStringT`personnages dans un .|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Retourne un pointeur aux `CSimpleStringT`caractères dans un , tronquant à la longueur spécifiée.|
|[CSimpleStringT::GetLength](#getlength)|Retourne le nombre de `CSimpleStringT` caractères dans un objet.|
|[CSimpleStringT::GetManager](#getmanager)|Récupère le responsable de `CSimpleStringT` la mémoire de l’objet.|
|[CSimpleStringT::GetString](#getstring)|Récupère la chaîne de caractères|
|[CSimpleStringT::IsEmpty](#isempty)|Teste `CSimpleStringT` si un objet ne contient pas de caractères.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Désactive le comptage des références et protège la chaîne dans le tampon.|
|[CSimpleStringT::Preallocate](#preallocate)|Alloue une quantité spécifique de mémoire pour le tampon de caractère.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Communiqués de contrôle `GetBuffer`de la mémoire tampon retournée par .|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Communiqués de contrôle `GetBuffer`de la mémoire tampon retournée par .|
|[CSimpleStringT::SetAt](#setat)|Définit un personnage à une position donnée.|
|[CSimpleStringT::SetManager](#setmanager)|Définit le gestionnaire `CSimpleStringT` de mémoire d’un objet.|
|[CSimpleStringT::SetString](#setstring)|Définit la chaîne `CSimpleStringT` d’un objet.|
|[CSimpleStringT::StringLength](#stringlength)|Retourne le nombre de caractères dans la chaîne spécifiée.|
|[CSimpleStringT::Truncate](#truncate)|Tronque la corde à une longueur spécifiée.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Permet le comptage des références et libère la chaîne dans le tampon.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleStringT::opérateur PCXSTR](#operator_pcxstr)|Accéde directement aux `CSimpleStringT` caractères stockés dans un objet sous forme de chaîne de style C.|
|[CSimpleStringT::operator\[\]](#operator_at)|Retourne le personnage à une position `GetAt`donnée — remplacement de l’opérateur pour .|
|[CSimpleStringT::opérateur](#operator_add_eq)|Concatenates une nouvelle chaîne à la fin d’une chaîne existante.|
|[CSimpleStringT::opérateur](#operator_eq)|Attribue une nouvelle valeur `CSimpleStringT` à un objet.|

### <a name="remarks"></a>Notes

`CSimpleStringT`est la classe de base pour les différentes classes de cordes soutenues par Visual C. Il fournit un soutien minimal pour la gestion de la mémoire de l’objet de chaîne et la manipulation de base de mémoire. Pour des objets à cordes plus avancés, voir [classe CStringT](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Spécifications

**En-tête:** atlsimpstr.h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT::Append

Annexe un `CSimpleStringT` objet à `CSimpleStringT` un objet existant.

### <a name="syntax"></a>Syntaxe

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Paramètres

*strSrc (strSrc)*<br/>
L’objet `CSimpleStringT` à annexer.

*pszSrc*<br/>
Un pointeur à une chaîne contenant les caractères à annexer.

*nLength (en)*<br/>
Nombre de caractères à ajouter.

### <a name="remarks"></a>Notes

Appelez cette méthode pour `CSimpleStringT` ajouter un `CSimpleStringT` objet existant à un autre objet.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::AppendChar

Annexe d’un personnage `CSimpleStringT` à un objet existant.

### <a name="syntax"></a>Syntaxe

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Paramètres

*Ch*<br/>
Le personnage à annexer

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter le caractère spécifié `CSimpleStringT` à la fin d’un objet existant.

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars

Copie d’un personnage `CSimpleStringT` ou d’un personnage à un objet.

### <a name="syntax"></a>Syntaxe

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Paramètres

*pchDest*<br/>
Un pointeur à une chaîne de caractère.

*pchSrc (en)*<br/>
Un pointeur à une chaîne contenant les caractères à copier.

*nChars (nChars)*<br/>
Le nombre de *caractères pchSrc* à copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier les caractères de *pchSrc* à la corde la *plus pchD.*

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

Copie d’un personnage `CSimpleStringT` ou d’un personnage à un objet.

### <a name="syntax"></a>Syntaxe

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Paramètres

*pchDest*<br/>
Un pointeur à une chaîne de caractère.

*pchSrc (en)*<br/>
Un pointeur à une chaîne contenant les caractères à copier.

*nChars (nChars)*<br/>
Le nombre de *caractères pchSrc* à copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier les caractères de *pchSrc* à la corde la *plus pchD.* Contrairement `CopyChars` `CopyCharsOverlapped` à , fournit une méthode sûre pour copier à partir de tampons de caractère qui pourraient être superposés.

### <a name="example"></a>Exemple

Voir l’exemple pour [CSimpleStringT::CopyChars](#copychars), `CSimpleStringT::SetString` ou le code source pour (situé dans atlsimpstr.h).

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>CSimpleStringT::CSimpleStringT

Construit un objet `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Paramètres

*strSrc (strSrc)*<br/>
Un `CSimpleStringT` objet existant à copier `CSimpleStringT` dans cet objet.

*pchSrc (en)*<br/>
Un pointeur à un tableau de caractères de longueur *nLength*, pas non annulé terminé.

*pszSrc*<br/>
Une corde à résilier `CSimpleStringT` nulle à copier dans cet objet.

*nLength (en)*<br/>
Un décompte du nombre `pch`de caractères dans .

*pStringMgr*<br/>
Un pointeur pour le `CSimpleStringT` gestionnaire de mémoire de l’objet. Pour plus `IAtlStringMgr` d’informations `CSimpleStringT`sur et la gestion de la mémoire pour , voir [Memory Management et CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Notes

Construire un `CSimpleStringT` nouvel objet. Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, des exceptions de mémoire peuvent en résulter.

### <a name="example"></a>Exemple

L’exemple suivant montre `CSimpleStringT::CSimpleStringT` l’utilisation de l’utilisation de l’ATL **typéef** `CSimpleString`. `CSimpleString`est une spécialisation couramment utilisée `CSimpleStringT`du modèle de classe .

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

## <a name="csimplestringtempty"></a><a name="empty"></a>CSimpleStringT::Vide

Fait `CSimpleStringT` de cet objet une ficelle vide et libère la mémoire au besoin.

### <a name="syntax"></a>Syntaxe

```
void Empty() throw();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Strings: CString Exception Cleanup](../cstring-exception-cleanup.md).

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra

Libère toute mémoire supplémentaire précédemment allouée par la chaîne mais n’est plus nécessaire.

### <a name="syntax"></a>Syntaxe

```
void FreeExtra();
```

### <a name="remarks"></a>Notes

Cela devrait réduire la mémoire au-dessus consommée par l’objet de chaîne. La méthode réaffecte le tampon à la longueur exacte retournée par [GetLength](#getlength).

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

La sortie de cet exemple est la suivante :

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Récupère la longueur allouée `CSimpleStringT` d’un objet.

### <a name="syntax"></a>Syntaxe

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de caractères alloués à cet objet.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer le nombre `CSimpleStringT` de caractères alloués à cet objet. Voir [FreeExtra](#freeextra) par exemple d’appeler cette fonction.

## <a name="csimplestringtgetat"></a><a name="getat"></a>CSimpleStringT::GetAt

Renvoie un `CSimpleStringT` personnage d’un objet.

### <a name="syntax"></a>Syntaxe

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Paramètres

*iChar (en)*<br/>
Index zéro du personnage de `CSimpleStringT` l’objet. Le paramètre *iChar* doit être supérieur ou égal à 0 et inférieur à la valeur retournée par [GetLength](#getlength). Sinon, `GetAt` générera une exception.

### <a name="return-value"></a>Valeur de retour

Un `XCHAR` qui contient le caractère à la position spécifiée dans la chaîne.

### <a name="remarks"></a>Notes

Appelez cette méthode pour retourner le seul personnage spécifié par *iChar*. Le sous-scriptum surchargé (**[]**) `GetAt`opérateur est un alias pratique pour . Le terminateur nul est adressable `GetAt`sans générer une exception en utilisant . Cependant, il n’est pas compté par `GetLength`, et la valeur retournée est de 0.

### <a name="example"></a>Exemple

L’exemple suivant montre `CSimpleStringT::GetAt`comment utiliser .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT::GetBuffer

Retourne un pointeur au tampon `CSimpleStringT` de caractère interne pour l’objet.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Paramètres

*nMinBufferLength*<br/>
Le nombre minimum de caractères que le tampon de caractère peut contenir. Cette valeur n’inclut pas l’espace pour un terminateur nul.

Si *nMinBufferLength* est plus grand que `GetBuffer` la longueur du tampon actuel, détruit le tampon actuel, le remplace par un tampon de la taille demandée, et réinitialise le nombre de références d’objet à zéro. Si vous avez déjà appelé [LockBuffer](#lockbuffer) sur ce tampon, vous perdez le verrou tampon.

### <a name="return-value"></a>Valeur de retour

Un `PXSTR` pointeur sur le tampon de caractère de l’objet (non terminé).

### <a name="remarks"></a>Notes

Appelez cette méthode pour retourner `CSimpleStringT` le contenu tampon de l’objet. Le `PXSTR` retour n’est pas une `CSimpleStringT` constante et permet donc une modification directe du contenu.

Si vous utilisez le `GetBuffer` pointeur retourné pour modifier le contenu de la `CSimpleStringT` chaîne, vous devez appeler [ReleaseBuffer](#releasebuffer) avant d’utiliser d’autres méthodes de membre.

L’adresse `GetBuffer` retournée par peut ne `ReleaseBuffer` pas `CSimpleStringT` être valide `CSimpleStringT` après l’appel à parce que les opérations supplémentaires peuvent causer le tampon d’être réaffecté. Le tampon n’est pas réaffecté si `CSimpleStringT`vous ne modifiez pas la longueur de la .

La mémoire tampon est `CSimpleStringT` automatiquement libérée lorsque l’objet est détruit.

Si vous gardez une trace de la longueur de la chaîne vous-même, vous ne devriez pas ajouter le caractère nul de fin. Toutefois, vous devez spécifier la longueur `ReleaseBuffer`finale de la chaîne lorsque vous relâchez le tampon avec . Si vous n’appendez pas un caractère nul de résiliation, vous devez passer -1 (la valeur par défaut) pour la longueur. `ReleaseBuffer`détermine ensuite la longueur du tampon.

S’il n’y `GetBuffer` a pas suffisamment de mémoire pour satisfaire la demande, cette méthode jette un CMemoryExceptionMD.

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

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Retourne un pointeur au tampon `CSimpleStringT` de caractère interne pour l’objet, tronquant ou augmentant sa longueur si nécessaire pour correspondre exactement à la longueur spécifiée dans *nLength*.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Paramètres

*nLength (en)*<br/>
La taille exacte `CSimpleStringT` du tampon de caractère dans les caractères.

### <a name="return-value"></a>Valeur de retour

Un `PXSTR` pointeur sur le tampon de caractère de l’objet (non terminé).

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer une longueur `CSimpleStringT` spécifiée du tampon interne de l’objet. Le `PXSTR` pointeur retourné **n’est** pas `CSimpleStringT` const et permet ainsi la modification directe du contenu.

Si vous utilisez le pointeur retourné par [GetBufferSetLength](#getbuffersetlength) pour modifier le contenu de la chaîne, appelez `ReleaseBuffer` pour mettre à jour l’état interne avant d’utiliser `CsimpleStringT` d’autres `CSimpleStringT` méthodes.

L’adresse `GetBufferSetLength` retournée par peut ne `ReleaseBuffer` pas `CSimpleStringT` être valide `CSimpleStringT` après l’appel à parce que les opérations supplémentaires peuvent causer le tampon d’être réaffecté. Le tampon n’est pas réaffecté si `CSimpleStringT`vous ne modifiez pas la longueur de la .

La mémoire tampon est `CSimpleStringT` automatiquement libérée lorsque l’objet est détruit.

Si vous gardez une trace de la longueur de la corde vous-même, n’appendicez pas le caractère nul de fin. Vous devez spécifier la longueur finale `ReleaseBuffer`de la chaîne lorsque vous relâchez le tampon en utilisant . Si vous n’appendez un caractère `ReleaseBuffer`nul de résiliation lorsque vous appelez, passez -1 (la valeur par défaut) pour la longueur à `ReleaseBuffer`, et `ReleaseBuffer` effectuera un `strlen` sur le tampon pour déterminer sa longueur.

Pour plus d’informations sur le comptage des références, voir les articles suivants :

- [Gérer les durées de vie des objets par](/windows/win32/com/managing-object-lifetimes-through-reference-counting) le comptage de référence dans le SDK Windows.

- [Mise en œuvre du comptage des références](/windows/win32/com/implementing-reference-counting) dans le SDK Windows.

- [Règles de gestion des comptes de référence](/windows/win32/com/rules-for-managing-reference-counts) dans le SDK Windows.

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

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT::GetLength

Retourne le nombre de `CSimpleStringT` caractères dans l’objet.

### <a name="syntax"></a>Syntaxe

```
int GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un compte des personnages de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette méthode pour retourner le nombre de caractères dans l’objet. Le décompte n’inclut pas un terminateur nul.

Pour les ensembles de caractères `GetLength` multioctets (MBCS), compte chaque caractère 8 bits; c’est-à-dire qu’un octet de plomb et de sentier dans un caractère multioctets est compté comme deux octets. Voir [FreeExtra](#freeextra) par exemple d’appeler cette fonction.

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT::GetManager

Récupère le responsable de `CSimpleStringT` la mémoire de l’objet.

### <a name="syntax"></a>Syntaxe

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur pour le `CSimpleStringT` gestionnaire de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le `CSimpleStringT` gestionnaire de mémoire utilisé par l’objet. Pour plus d’informations sur les gestionnaires de mémoire et les objets à chaîne, voir [Memory Management et CStringT](../memory-management-with-cstringt.md).

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT::GetString

Récupère la chaîne de caractères.

### <a name="syntax"></a>Syntaxe

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à une chaîne de caractères non terminée.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer la `CSimpleStringT` chaîne de caractères associée à l’objet.

> [!NOTE]
> Le `PCXSTR` pointeur retourné est **const** et `CSimpleStringT` ne permet pas la modification directe du contenu.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>CSimpleStringT::IsEmpty

Teste `CSimpleStringT` un objet pour l’état vide.

### <a name="syntax"></a>Syntaxe

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI `CSimpleStringT` si l’objet a 0 longueur; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer si l’objet contient une chaîne vide.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>CSimpleStringT::LockBuffer

Désactive le comptage des références et protège la chaîne dans le tampon.

### <a name="syntax"></a>Syntaxe

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CSimpleStringT` à un objet ou une corde non terminée.

### <a name="remarks"></a>Notes

Appelez cette méthode pour verrouiller `CSimpleStringT` le tampon de l’objet. En `LockBuffer`appelant, vous créez une copie de la chaîne, avec un -1 pour le nombre de références. Lorsque la valeur de compte de référence est de -1, la chaîne dans le tampon est considérée comme étant dans un état « verrouillé ». Alors qu’elle est en état de verrouillée, la chaîne est protégée de deux façons :

- Aucune autre chaîne ne peut obtenir une référence aux données dans la chaîne verrouillée, même si cette chaîne est attribuée à la chaîne verrouillée.

- La corde verrouillée ne fera jamais référence à une autre corde, même si cette autre corde est copiée sur la corde verrouillée.

En verrouillant la chaîne dans le tampon, vous vous assurez que l’emprise exclusive de la chaîne sur le tampon restera intacte.

Une fois que `LockBuffer`vous avez terminé avec , appelez [UnlockBuffer](#unlockbuffer) pour réinitialiser le nombre de références à 1.

> [!NOTE]
> Si vous appelez [GetBuffer](#getbuffer) sur un `GetBuffer` tampon `nMinBufferLength` verrouillé et que vous définissez le paramètre à plus de la longueur du tampon actuel, vous perdrez le verrou tampon. Un tel `GetBuffer` appel pour détruire le tampon actuel, le remplace par un tampon de la taille demandée, et réinitialise le nombre de références à zéro.

Pour plus d’informations sur le comptage des références, voir les articles suivants :

- [Gérer les durées de vie des objets grâce au comptage de référence](/windows/win32/com/managing-object-lifetimes-through-reference-counting) dans le SDK Windows

- [Mise en œuvre du comptage des références](/windows/win32/com/implementing-reference-counting) dans le SDK Windows

- [Règles de gestion des comptes de référence](/windows/win32/com/rules-for-managing-reference-counts) dans le SDK Windows

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

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT::opérateur\[\]

Appelez cette fonction pour accéder à un seul caractère du tableau de caractères.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Paramètres

*iChar (en)*<br/>
Index zéro d’un personnage dans la chaîne.

### <a name="remarks"></a>Notes

L’opérateur surchargé de sous-scripte **([]**) renvoie un seul caractère spécifié par l’indice zéro dans *iChar*. Cet opérateur remplace la fonction [membre GetAt.](#getat)

> [!NOTE]
> Vous pouvez utiliser le sous-scriptum (**[]**) `CSimpleStringT`opérateur pour obtenir la valeur d’un personnage `CSimpleStringT`dans un , mais vous ne pouvez pas l’utiliser pour changer la valeur d’un personnage dans un .

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT::opérateur\[\]

Appelez cette fonction pour accéder à un seul caractère du tableau de caractères.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Paramètres

*iChar (en)*<br/>
Index zéro d’un personnage dans la chaîne.

### <a name="remarks"></a>Notes

L’opérateur surchargé de sous-scripte **([]**) renvoie un seul caractère spécifié par l’indice zéro dans *iChar*. Cet opérateur remplace la fonction [membre GetAt.](#getat)

> [!NOTE]
> Vous pouvez utiliser le sous-scriptum (**[]**) `CSimpleStringT`opérateur pour obtenir la valeur d’un personnage `CSimpleStringT`dans un , mais vous ne pouvez pas l’utiliser pour changer la valeur d’un personnage dans un .

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT::opérateur

Rejoint une nouvelle chaîne ou un nouveau personnage jusqu’à la fin d’une chaîne existante.

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
Un pointeur à une corde non terminée.

*strSrc (strSrc)*<br/>
Un pointeur `CSimpleStringT` vers un objet existant.

*Ch*<br/>
Caractère à ajouter.

### <a name="remarks"></a>Notes

L’opérateur accepte `CSimpleStringT` un autre objet ou un personnage. Notez que des exceptions de mémoire peuvent se produire chaque fois que vous `CSimpleStringT` utilisez cet opérateur de concatenation parce que le nouveau stockage peut être alloué pour les caractères ajoutés à cet objet.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT::opérateur

Attribue une nouvelle valeur `CSimpleStringT` à un objet.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Paramètres

*pszSrc*<br/>
Un pointeur à une corde non terminée.

*strSrc (strSrc)*<br/>
Un pointeur `CSimpleStringT` vers un objet existant.

### <a name="remarks"></a>Notes

Si la chaîne de destination (le côté gauche) est déjà assez grande pour stocker les nouvelles données, aucune nouvelle allocation de mémoire n’est effectuée. Notez que des exceptions de mémoire peuvent se produire chaque fois `CSimpleStringT` que vous utilisez l’opérateur d’affectation parce que le nouveau stockage est souvent alloué pour contenir l’objet résultant.

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

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT::opérateur PCXSTR

Accéde directement aux `CSimpleStringT` caractères stockés dans un objet sous forme de chaîne de style C.

### <a name="syntax"></a>Syntaxe

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de caractère aux données de la chaîne.

### <a name="remarks"></a>Notes

Aucun personnage n’est copié; seul un pointeur est retourné. Soyez prudent avec cet opérateur. Si vous `CString` changez d’objet après avoir obtenu le pointeur de caractère, vous pouvez provoquer une réaffectation de la mémoire qui invalide le pointeur.

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

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::PCXSTR

Un pointeur à une chaîne constante.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::Preallocate

Alloue une quantité spécifique `CSimpleStringT` d’octets pour l’objet.

### <a name="syntax"></a>Syntaxe

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Paramètres

*nLength (en)*<br/>
La taille exacte `CSimpleStringT` du tampon de caractère dans les caractères.

### <a name="remarks"></a>Notes

Appelez cette méthode pour allouer `CSimpleStringT` une taille tampon spécifique pour l’objet.

`CSimpleStringT`génère une STATUS_NO_MEMORY exception si elle n’est pas en mesure d’allouer de l’espace pour le tampon de caractère. Par défaut, l’allocation de mémoire est `HeapAlloc` effectuée `HeapReAlloc`par win32 fonctions API ou .

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT::PXSTR

Un pointeur à une chaîne.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Communiqués de contrôle de la mémoire tampon allouée par [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Paramètres

*nNewLength (en)*<br/>
La nouvelle longueur de la chaîne en caractères, sans compter un terminateur nul. Si la chaîne est non terminée, la `CSimpleStringT` valeur par défaut de -1 définit la taille jusqu’à la longueur actuelle de la chaîne.

### <a name="remarks"></a>Notes

Appelez cette méthode pour réaffecter ou libérer le tampon de l’objet de chaîne. Si vous savez que la chaîne dans le tampon est non terminée, vous pouvez omettre *l’argument nNewLength.* Si votre chaîne n’est pas non annulée, utilisez *nNewLength* pour spécifier sa longueur. L’adresse retournée par [GetBuffer](#getbuffer) est `ReleaseBuffer` invalide `CSimpleStringT` après l’appel à ou toute autre opération.

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

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Communiqués de contrôle de la mémoire tampon allouée par [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Paramètres

*nNewLength (en)*<br/>
La longueur de la corde libérée

### <a name="remarks"></a>Notes

Cette fonction est fonctionnellement similaire à [ReleaseBuffer,](#releasebuffer) sauf qu’une longueur valide pour l’objet de chaîne doit être passée.

## <a name="csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT::SetAt

Définit un personnage `CSimpleStringT` unique à partir d’un objet.

### <a name="syntax"></a>Syntaxe

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Paramètres

*iChar (en)*<br/>
Index zéro du personnage de `CSimpleStringT` l’objet. Le paramètre *iChar* doit être supérieur ou égal à 0 et inférieur à la valeur retournée par [GetLength](#getlength).

*Ch*<br/>
Le nouveau personnage.

### <a name="remarks"></a>Notes

Appelez cette méthode pour remplacer le personnage situé à *iChar*. Cette méthode n’agrandira pas la chaîne si *iChar* dépasse les limites de la chaîne existante.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT::SetManager

Spécifie le `CSimpleStringT` responsable de la mémoire de l’objet.

### <a name="syntax"></a>Syntaxe

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Paramètres

*pStringMgr*<br/>
Un pointeur pour le nouveau gestionnaire de mémoire.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier `CSimpleStringT` un nouveau gestionnaire de mémoire utilisé par l’objet. Pour plus d’informations sur les gestionnaires de mémoire et les objets à chaîne, voir [Memory Management et CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT::SetString

Définit la chaîne `CSimpleStringT` d’un objet.

### <a name="syntax"></a>Syntaxe

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Paramètres

*pszSrc*<br/>
Un pointeur à une corde non terminée.

*nLength (en)*<br/>
Un décompte du nombre de personnages dans *pszSrc*.

### <a name="remarks"></a>Notes

Copiez une `CSimpleStringT` ficelle dans l’objet. `SetString`surmene les données de chaîne plus anciennes dans le tampon.

Les deux `SetString` versions de vérifier si *pszSrc* est un pointeur nul, et si elle est, jeter une erreur de E_INVALIDARG.

La version à `SetString` un paramètre de s’attend *pszSrc* à pointer vers une chaîne non terminée.

La version à `SetString` deux paramètres de s’attend également *pszSrc* à être une chaîne à durée nulle. Il utilise *nLength* comme longueur de chaîne à moins qu’il rencontre un terminateur nul d’abord.

La version à `SetString` deux paramètres de vérifie également si *pszSrc* indique un emplacement dans le tampon actuel dans `CSimpleStringT`. Dans ce cas `SetString` particulier, utilise une fonction de copie mémoire qui ne surcorite pas les données de chaîne car elle copie les données de chaîne à son tampon.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>CSimpleStringT::StringLength

Retourne le nombre de caractères dans la chaîne spécifiée.

### <a name="syntax"></a>Syntaxe

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Paramètres

*Zsp*<br/>
Un pointeur à une corde non terminée.

### <a name="return-value"></a>Valeur de retour

Le nombre de caractères dans *psz*; sans compter un terminateur nul.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre de caractères dans la chaîne pointée par *psz*.

### <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT::Truncate

Tronque la corde à la nouvelle longueur.

### <a name="syntax"></a>Syntaxe

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Paramètres

*nNewLength (en)*<br/>
La nouvelle longueur de la corde.

### <a name="remarks"></a>Notes

Appelez cette méthode pour tronquer le contenu de la chaîne à la nouvelle longueur.

> [!NOTE]
> Cela n’affecte pas la longueur allouée du tampon. Pour diminuer ou augmenter le tampon actuel, voir [FreeExtra](#freeextra) et [Preallocate](#preallocate).

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

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

Déverrouiller le `CSimpleStringT` tampon de l’objet.

### <a name="syntax"></a>Syntaxe

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour réinitialiser le nombre de références de la chaîne à 1.

Le `CSimpleStringT` destructeur appelle `UnlockBuffer` automatiquement pour s’assurer que le tampon n’est pas verrouillé lorsque le destructeur est appelé. Pour un exemple de cette méthode, voir [LockBuffer](#lockbuffer).

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT: :CSimpleStringT

Détruit un objet `CSimpleStringT` .

### <a name="syntax"></a>Syntaxe

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Notes

Appelez cette méthode `CSimpleStringT` pour détruire l’objet.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
