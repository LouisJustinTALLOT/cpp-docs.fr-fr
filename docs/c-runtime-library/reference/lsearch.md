---
title: _lsearch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lsearch
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch
- lsearch
dev_langs:
- C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2aaf6626b2f7005181640f77026b6924c39cd325
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451297"
---
# <a name="lsearch"></a>_lsearch

Effectue une recherche linéaire portant sur une valeur ; l’ajoute en fin de liste si elle est introuvable. Une version plus sécurisée de cette fonction est disponible. Consultez [_lsearch_s](lsearch-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Objet à rechercher.

*base*<br/>
Pointeur désignant la base du tableau à explorer.

*Nombre*<br/>
Nombre d'éléments.

*width*<br/>
Largeur de chaque élément du tableau.

*compare*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est un pointeur désignant la clé pour la recherche. Le second paramètre est un pointeur désignant un élément de tableau à comparer à la clé.

## <a name="return-value"></a>Valeur de retour

Si la clé est trouvée, **_lsearch** retourne un pointeur vers l’élément du tableau à *base* qui correspond à *clé*. Si la clé est introuvable, **_lsearch** retourne un pointeur vers l’élément qui vient d’être ajouté à la fin du tableau.

## <a name="remarks"></a>Notes

Le **_lsearch** fonction effectue une recherche linéaire pour la valeur *clé* dans un tableau de *nombre* éléments, chacun des *largeur* octets. Contrairement aux **bsearch**, **_lsearch** ne nécessite pas de tableau à trier. Si *clé* n’est trouvé, **_lsearch** ajoute à la fin du tableau et incrémente *nombre*.

Le *comparer* argument est un pointeur vers une routine fournie par l’utilisateur qui compare deux éléments du tableau et retourne une valeur précisant leur relation. **_lsearch** appelle la *comparer* routine une ou plusieurs fois lors de la recherche, le passage de pointeurs vers deux éléments de tableau à chaque appel. *comparer* doit comparer les éléments et de retour soit différent de zéro (ce qui signifie que les éléments sont différents), ou 0 (ce qui signifie que les éléments sont identiques).

Cette fonction valide ses paramètres. Si *comparer*, *clé* ou *nombre* est **NULL**, ou si *base* est **NULL**et *nombre* est différent de zéro, ou si *largeur* est inférieur à zéro, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **NULL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_lsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main(void)
{
   char * wordlist[4] = { "hello", "thanks", "bye" };
                            // leave room to grow...
   int n = 3;
   char **result;
   char *key = "extra";
   int i;

   printf( "wordlist before _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );

   result = (char **)_lsearch( &key, wordlist,
                      &n, sizeof(char *), compare );

   printf( "wordlist after _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );
}

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}
```

```Output
wordlist before _lsearch: hello thanks bye
wordlist after _lsearch: hello thanks bye extra
```

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
