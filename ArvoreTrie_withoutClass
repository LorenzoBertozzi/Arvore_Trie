#include <bits/stdc++.h>

using namespace std;

#define CHAR_SIZE 128

typedef struct trie
{
    bool isFolha;
    trie* letra[CHAR_SIZE];
} trie;

void construtor(trie* trie)
{
    trie->isFolha = false;

    for(int i = 0; i < CHAR_SIZE; i++)
    {
        trie->letra[i] = NULL;
    }
}

void insert(trie* arvore, string chave);
bool buscar(trie* arvore, string chave);
bool temFilha(const trie* aux);
bool delet(trie*& arvore, string chave);

int main()
{
    trie* arvore = new trie();
    construtor(arvore);

    insert(arvore, "hello");
    cout << buscar(arvore, "hello") << " ";

    insert(arvore, "helloworld");
    cout << buscar(arvore, "helloworld") << " ";

    insert(arvore, "h");
    cout << buscar(arvore, "h") << " ";

    return 0;
}

void insert(trie* arvore, string chave)
{
    trie* aux = arvore;
    for(int i = 0; i < chave.length(); i++)
    {
        if(aux->letra[chave[i]] == NULL)
        {
            aux->letra[chave[i]] = new trie();
        }
        aux = aux->letra[chave[i]];
    }
    aux->isFolha = true;
}

bool buscar(trie* arvore, string chave)
{
    if(arvore == NULL)
    {
        return false;
    }

    trie* aux = arvore;

    for(int i = 0; i < chave.length(); i++)
    {
        aux = aux->letra[chave[i]];

        if(aux == NULL)
        {
            return false;
        }
    }
    return aux->isFolha;
}

bool temFilha(const trie* aux)
{
    for(int i = 0; i < CHAR_SIZE; i++)
    {
        if(aux->letra[i])
        {
            return true;
        }
    }
    return false;
}

bool delet(trie*& arvore, string chave)
{
    trie* aux = arvore;

    if(aux == NULL)
    {
        return false;
    }

    if(chave.length() > 0)
    {
        if(aux->letra[chave[0]] != NULL && delet(aux->letra[chave[0]], chave.substr(1)) && aux->isFolha == false)
        {
            if(!temFilha(aux))
            {
                delete aux;
                aux = NULL;
                return true;
            }
            else
            {
                return false;
            }
        }
    }

    if(chave.length() == 0 && aux->isFolha)
    {
        if(!temFilha(aux))
        {
            delete aux;
            arvore = NULL;

            return true;
        }
        else
        {
            aux->isFolha = false;

            return false;
        }
    }
    return false;
}
