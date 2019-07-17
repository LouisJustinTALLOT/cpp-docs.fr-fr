---
title: _set_se_translator
ms.date: 02/21/2018
apiname:
- _set_se_translator
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
apitype: DLLExport
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 23eb4e9016666567771832cefed686cb9197b02f
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299709"
---
# <a name="setsetranslator"></a>_set_se_translator

Définissez une fonction de rappel par thread pour traduire des exceptions Win32 (exceptions structurées C C++ ) en exceptions typées.

## <a name="syntax"></a>Syntaxe

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Paramètres

*seTransFunction*<br/>
Pointeur vers une fonction de traduction d'exceptions structurées C que vous écrivez.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la précédente fonction de traduction enregistrée par _ **set_se_translator**, afin que la fonction précédente puisse être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut; Cette valeur peut être **nullptr**.

## <a name="remarks"></a>Notes

La fonction _ **set_se_translator** fournit un moyen de gérer les exceptions Win32 (exceptions structurées C++ C) en tant qu’exceptions typées. Pour que chaque exception c soit gérée par un C++ gestionnaire **catch** , définissez d’abord une classe wrapper d’exceptions c qui peut être utilisée, ou dérivée de, pour attribuer un type de classe spécifique à une exception c. Pour utiliser cette classe, installez une fonction de traduction d'exception C personnalisée appelée par le mécanisme de gestion des exceptions interne chaque fois qu'une exception C est levée. Dans votre fonction de traduction, vous pouvez lever n’importe quelle exception typée qui peut être C++ interceptée par un gestionnaire **catch** correspondant.

Vous devez utiliser [/EHa](../../build/reference/eh-exception-handling-model.md) lors de l’utilisation de _ **set_se_translator**.

Pour spécifier une fonction de traduction personnalisée, appelez _ **set_se_translator** en utilisant le nom de votre fonction de traduction comme argument. La fonction de traduction que vous écrivez est appelée une fois pour chaque appel de fonction sur la pile qui a des blocs **try** . Il n'existe aucune fonction de traduction par défaut.

Votre fonction de traduction se contente de lever une exception typée C++. Si elle effectue d'autres actions (écrire dans un fichier journal, par exemple), votre programme risque de ne pas se comporter comme prévu, car le nombre de fois où la fonction de traduction est appelée dépend de la plateforme.

Dans un environnement multithread, les fonctions de traduction sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction de traduction. Par conséquent, chaque thread est responsable de sa propre gestion de traduction. _ **set_se_translator** est spécifique à un thread; une autre DLL peut installer une fonction de traduction différente.

La fonction *seTransFunction* que vous écrivez doit être une fonction compilée native (non compilée avec/CLR). Il doit prendre un entier non signé et un pointeur vers une structure **_EXCEPTION_POINTERS** Win32 comme arguments. Les arguments sont les valeurs de retour des appels aux fonctions API Win32 **GetExceptionCode** et **GetExceptionInformation** , respectivement.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Pour _ **set_se_translator**, il y a des implications lors de la liaison dynamique au CRT; une autre DLL du processus peut appeler _ **set_se_translator** et remplacer votre gestionnaire par le sien.

Lorsque vous utilisez _ **set_se_translator** à partir du code managé (code compilé avec/CLR) ou du code natif et managé mixte, sachez que le traducteur affecte les exceptions générées uniquement en code natif. Les exceptions managées générées en code managé (par exemple, en déclenchant `System::Exception`) ne sont pas acheminées par le biais de la fonction de traduction. Les exceptions levées dans le code managé à l’aide de la fonction Win32 **RaiseException** ou provoquées par une exception système telle qu’une exception de division par zéro sont acheminées via le traducteur.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple encapsule les appels pour définir un traducteur d’exceptions structurées et pour restaurer l’ancien dans une classe RAII `Scoped_SE_Translator`,. Cette classe vous permet d’introduire un traducteur spécifique à l’étendue comme une déclaration unique. Le destructeur de classe restaure le convertisseur d’origine lorsque le contrôle quitte l’étendue.

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Exemple

Bien que les fonctionnalités fournies par _ **set_se_translator** ne soient pas disponibles dans le code managé, il est possible d’utiliser ce mappage en code natif, même si ce code natif se trouve dans une compilation sous le commutateur **/CLR** , tant que le code natif est indiqué à `#pragma unmanaged`l’aide de. Si une exception structurée est levée dans le code managé qui doit être mappé, le code qui génère et gère l’exception doit être marqué `#pragma unmanaged`. Le code suivant illustre une utilisation possible. Pour plus d’informations, consultez [Directives pragma et mot clé __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
