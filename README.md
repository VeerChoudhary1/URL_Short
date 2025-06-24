# URL_Short
import random
import string

DB = {}


# version - 1

def getShortURL(LongURL):
    """
    It will generate short URL
    """

    length = random.randint(4,7)
    chars = string.ascii_lowercase
    shortURL = "".join([random.choice(chars) for i in range(length)])

    if shortURL in DB:
        return getShortURL(LongURL)
    else:
        DB[shortURL] = LongURL

    return "cm.in/" + shortURL
# version 2
import string
import random

DB = {}


def getShortURL(longURL, myShortURL = None):
    """
    It will provide you short URL
    """
    if myShortURL:
        if myShortURL in DB:
            return "Given ShortURL already exist" 
        else:
            DB[myShortURL] = longURL
            res = "cm.in/" + myShortURL

            return res 
    length = random.randint(4, 7)
    chars = string.ascii_lowercase + string.digits

    shortURL = "".join([random.choice(chars) for i in range(length)])

    if shortURL in DB:
        return getShortURL(longURL)
    else:
        DB[shortURL] = longURL
    
    result = "cm.in/" + shortURL
    return result


def updateLongURL(shortURL, newLongURL):
    """
    It will update longURL 
    """
    if shortURL in DB:
        shortURL = shortURL.split("/")[-1]
        DB[shortURL] = newLongURL
        res = "cm.in/" + shortURL
        return res 
    else:
        return "ShortURL doesn't exist"

