---
title: 'Comment : Interface entre le Code Non exceptionnel et exceptionnel | Microsoft Docs'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74805c7ecd4b4ecef71d8ac1358fd6c2014e27d5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940116"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Comment : établir une interface entre le code exceptionnel et le code non exceptionnel
Cet article explique comment implémenter une gestion cohérente des exceptions dans un module C++, et comment convertir ces exceptions vers et depuis des codes d'erreur aux limites de l'exception.  
  
 Parfois, un module C++ doit interagir avec du code qui n'utilise pas d'exceptions (code non exceptionnel). Une telle interface est appelée un *limite d’exception*. Par exemple, vous pouvez appeler la fonction Win32 `CreateFile` dans votre programme C++. La fonction `CreateFile` ne lève pas d'exception ; en revanche, elle définit des codes d'erreur qui peuvent être récupérés par la fonction `GetLastError`. Si votre programme C++ est non trivial, vous préférez probablement appliquer une stratégie cohérente de gestion des erreurs basée sur les exceptions. En outre, vous ne souhaitez probablement pas abandonner les exceptions simplement parce que vous interagissez avec du code non-exceptionnel, ni combiner des stratégies de gestion des erreurs basées sur des exceptions et non basées sur des exceptions dans votre module C++.  
  
## <a name="calling-non-exceptional-functions-from-c"></a>Appel de fonctions non exceptionnelles depuis C++  
 Lorsque vous appelez une fonction non exceptionnelle depuis C++, l'idée est d'encapsuler cette fonction dans une fonction C++ qui détecte les erreurs et lève éventuellement une exception. Lorsque vous concevez cette fonction wrapper, choisissez d'abord le type de garantie d'exception à fournir : pas de levée, fort ou de base. Ensuite, créez la fonction de manière à ce que toutes les ressources, par exemple, les handles de fichiers, soient correctement libérées si une exception est levée. En général, cela signifie que vous utilisez des pointeurs intelligents ou des gestionnaires de ressources semblables pour posséder les ressources. Pour plus d’informations sur les considérations de conception, consultez [Comment : conception pour la sécurité de l’Exception](../cpp/how-to-design-for-exception-safety.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant illustre les fonctions C++ qui utilisent les fonctions Win32 `CreateFile` et `ReadFile` en interne pour ouvrir et lire deux fichiers.  La classe `File` est un wrapper RAII (Resource Acquisition Is Initialization) pour les handles de fichiers. Son constructeur détecte un état "fichier introuvable" et lève une exception pour propager l'erreur en haut de la pile des appels du module C++ (dans cet exemple, la fonction `main()`). Si une exception est levée après qu'un objet `File` est entièrement construit, le destructeur appelle automatiquement `CloseHandle` pour libérer le handle de fichiers. (Si vous préférez, vous pouvez utiliser la classe ALT (Active Template Library) `CHandle` dans le même but, ou `unique_ptr` avec un programme de suppression personnalisé). Les fonctions qui appellent les API Win32 et CRT détectent les erreurs et lèvent des exceptions C++ à l'aide de la fonction définie localement `ThrowLastErrorIf`, qui à son tour utilise la classe `Win32Exception`, dérivée de la classe `runtime_error`. Toutes les fonctions contenues dans cet exemple fournissent une garantie d'exception de type fort ; si une exception est levée à tout moment dans ces fonctions, aucune ressource n'est perdue et aucun état de programme n'est modifié.  
  
```cpp  
// compile with: /EHsc  
#include <Windows.h>  
#include <stdlib.h>  
#include <vector>  
#include <iostream>  
#include <string>  
#include <limits>  
#include <stdexcept>  
  
using namespace std;  
  
string FormatErrorMessage(DWORD error, const string& msg)  
{  
    static const int BUFFERLENGTH = 1024;  
    vector<char> buf(BUFFERLENGTH);  
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),   
        BUFFERLENGTH - 1, 0);   
    return string(buf.data()) + "   ("  + msg  + ")";  
}  
  
class Win32Exception : public runtime_error  
{      
private:  
    DWORD m_error;  
public:  
    Win32Exception(DWORD error, const string& msg)  
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }  
  
    DWORD GetErrorCode() const { return m_error; }  
};  
  
void ThrowLastErrorIf(bool expression, const string& msg)   
{   
    if (expression) {   
        throw Win32Exception(GetLastError(), msg);   
    }   
}   
  
class File  
{  
private:  
    HANDLE m_handle;  
  
    // Declared but not defined, to avoid double closing.  
    File& operator=(const File&);  
    File(const File&);  
public:  
    explicit File(const string& filename)   
    {  
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,   
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);  
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,   
            "CreateFile call failed on file named " + filename);  
    }  
  
    ~File() { CloseHandle(m_handle); }  
  
    HANDLE GetHandle() { return m_handle; }  
};  
  
size_t GetFileSizeSafe(const string& filename)  
{  
    File fobj(filename);  
    LARGE_INTEGER filesize;  
  
    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);  
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);  
  
    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {  
        return filesize.QuadPart;  
    } else {  
        throw;   
    }  
}  
  
vector<char> ReadFileVector(const string& filename)  
{  
    File fobj(filename);  
    size_t filesize = GetFileSizeSafe(filename);  
    DWORD bytesRead = 0;  
  
    vector<char> readbuffer(filesize);  
  
    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),   
        &bytesRead, nullptr);  
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);  
  
    cout << filename << " file size: " << filesize << ", bytesRead: "   
        << bytesRead << endl;  
  
    return readbuffer;  
}  
  
bool IsFileDiff(const string& filename1, const string& filename2)   
{  
    return ReadFileVector(filename1) != ReadFileVector(filename2);  
}   
  
#include <iomanip>  
  
int main ( int argc, char* argv[] )  
{  
    string filename1("file1.txt");  
    string filename2("file2.txt");  
  
    try  
    {  
        if(argc > 2) {  
            filename1 = argv[1];  
            filename2 = argv[2];  
        }   
  
        cout << "Using file names " << filename1 << " and " << filename2 << endl;  
  
        if (IsFileDiff(filename1, filename2)) {  
            cout << "*** Files are different." << endl;  
        } else {  
            cout<< "*** Files match." << endl;  
        }  
    }  
    catch(const Win32Exception& e)  
    {          
        ios state(nullptr);  
        state.copyfmt(cout);  
        cout << e.what() << endl;  
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')   
            << e.GetErrorCode() << endl;  
        cout.copyfmt(state); // restore previous formatting  
    }  
}  
  
```  
  
## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Appel de code exceptionnel depuis un code non exceptionnel  
 Les fonctions C++ déclarées comme "C externes" peuvent être appelées par des programmes C. Les serveurs COM C++ peuvent être utilisés par du code écrit dans plusieurs langages différents. Lorsque vous implémentez des fonctions publiques prenant en charge les exceptions en C++ pour qu'elles soient appelées par du code non exceptionnel, la fonction C++ ne doit pas autoriser les exceptions à se propager à l'appelant. Par conséquent, la fonction C++ doit spécifiquement intercepter chaque exception qu'elle sait gérer et, le cas échéant, convertir l'exception en un code d'erreur que l'appelant comprend. Si toutes les exceptions potentielles ne sont pas connues, la fonction C++ doit avoir un bloc `catch(...)` comme dernier gestionnaire. Dans ce cas, il est préférable de signaler une erreur irrécupérable à l'appelant, car votre programme peut être dans un état inconnu.  
  
 L'exemple suivant illustre une fonction qui suppose qu'une exception pouvant être levée est une exception Win32Exception ou un type d'exception dérivé de `std::exception`. La fonction intercepte toute exception de ces types et propage les informations d'erreur sous la forme d'un code d'erreur Win32 à l'appelant.  
  
```cpp  
BOOL DiffFiles2(const string& file1, const string& file2)   
{   
    try   
    {   
        File f1(file1);   
        File f2(file2);   
        if (IsTextFileDiff(f1, f2))   
        {   
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);   
            return FALSE;   
        }   
        return TRUE;   
    }   
    catch(Win32Exception& e)   
    {   
        SetLastError(e.GetErrorCode());   
    }  
  
    catch(std::exception& e)   
    {   
        SetLastError(MY_APPLICATION_GENERAL_ERROR);   
    }   
    return FALSE;   
}  
  
```  
  
 Lorsque vous convertissez des exceptions en codes d'erreur, un problème potentiel est que les codes d'erreur ne contiennent pas souvent toutes les informations qu'une exception peut stocker. Pour résoudre ce problème, vous pouvez fournir un **catch** bloc pour chaque type d’exception spécifique qui peut être levée et d’exécuter la journalisation pour enregistrer les détails de l’exception avant qu’il est converti en un code d’erreur. Cette approche peut créer un grand nombre de répétition de code si plusieurs fonctions utilisent toutes le même ensemble de **catch** blocs. Un bon moyen pour éviter la répétition de code consiste à refactoriser ces blocs dans une fonction utilitaire privée qui implémente le **essayez** et **catch** bloque et accepte un objet de fonction qui est appelé dans le **essayez** bloc. Dans chaque fonction publique, passez le code à la fonction utilitaire en tant qu’expression lambda.  
  
```cpp  
template<typename Func>   
bool Win32ExceptionBoundary(Func&& f)   
{   
    try   
    {   
        return f();   
    }   
    catch(Win32Exception& e)   
    {   
        SetLastError(e.GetErrorCode());   
    }   
    catch(const std::exception& e)   
    {   
        SetLastError(MY_APPLICATION_GENERAL_ERROR);   
    }   
    return false;   
}  
  
```  
  
 L’exemple suivant montre comment écrire l’expression lambda qui définit le foncteur. Lorsqu’un foncteur est défini "inline" à l’aide d’une expression lambda, il est souvent plus facile à lire que s’il avait été écrit en tant qu’objet de fonction nommé.  
  
```cpp  
bool DiffFiles3(const string& file1, const string& file2)   
{   
    return Win32ExceptionBoundary([&]() -> bool  
    {   
        File f1(file1);   
        File f2(file2);   
        if (IsTextFileDiff(f1, f2))   
        {   
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);   
            return false;   
        }   
        return true;   
    });   
}  
  
```  
  
 Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs et exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Guide pratique de conception pour la sécurité des exceptions](../cpp/how-to-design-for-exception-safety.md)