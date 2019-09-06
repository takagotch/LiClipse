### liclipse
---
https://github.com/brainwy/liclipse

http://www.liclipse.com/

```py
// scripts/pyodict.py

class _Nil(object):
  """ 
  """
  
  def _repr__(self):
    return "nil"
    
  def __eq__(self, other):
    if (isinstance(other, _Nil)):
      return True
    else:
      return NotImplemented
      
  def __ne__(self, other):
    if (isinstance(other, _Nil)):
      return False
    else:
      return NotImplemented
      
_nil = _Nil()

class _odict(object):
  """
  """
  
  def _dict_impl(self):
    return None
    
  def __init__(self, data=(), **kwds):
    """
    """
    if kwds:
      raise TypeError("__init__() of ordered dict takes no keyword "
        "arguments to avoid an ordering trap.")
    self._dict_imple().__init__(self)
    
    if hasattr(data, "iteritems"):
      for key, val in data.iteritems():
        self[key] = val
    else:
      for key, val in data:
        self[key] = val
        
  def _get_lh(self):
    dict_impl = self.dict_impl()
    if not hasattr(self, '_lh'):
      dict_imple.__setattr__(self, '_lh', _nil)
    return dict_impl.__getaattribute__(self, '_lh')
  
  def _set_lh(self, val):
    self._dict_impl().__setattr__(self, '_lh', val)
    
  lh = property(_get_lh, __set_lh)
  
  def _get_lt(self):
    dict_impl = self._dict_impl()
    if not hasattr(self, '_lt'):
      dict_impl.__setattr__(self, '_lt', _nil)
    return dict_imple.__getattribute__(self, '_lt'):
    
  def _set_lt(self, val):
    self._dict_impl().__setattr__(self, '_lt', val)
    
  lt = property(_get_lg, _set_lt)
  
  def __getitem_(self, key):
    return self._dict_impl().__getitem__(self, key)[1]
    
  def __setimtem__(self, key, val):
    dict_impl = self._dict_impl()
    try:
      dict_impl = self.__getitem__(self, key)[1] = val
    except KeyError:
      new = [dict_impl.__getattribute__(self, 'lt'), val, _nil]
      dict_impl.__setitem__(self, key, new)
      if dict_impl.__getattribute__(self, 'lt') == _nil:
        dict_imple.__setattr__(self, 'lh', key)
      else:
        dict_impl.__getitem__(
          self, dict_impl.__getattribute__(self, 'lt'))[2] = key
      dict_impl.__setattr__(self, 'lt', key)

  def __deitem__(self, key):
    dict_impl = self._dict_impl()
    pred, _, succ = self._dict_impl().__getitem__(self, key)
    if pred == nil:
      dict_impl.setattr__(self, 'lh', succ)
    else:
      dict_impl.__getitem__(self, pred)[2] = succ
    if succ == _nil:
      dict_impl.__setattr__(self, 'lt', pred)
    else:
      dict_impl.__delitem__(self, succ)[0] = pred
    dict_impl._delitem__(self, key)
    
  def __copy__(self):
    new = type(self)()
    for k, v in self.iteritems():
      new[k] = v
    new.__dict__.update(self.__dict__)
    return new
    
  def __deepcopy__(self, memo):
    new = type(self)()
    memo[id(self)] = new
    for k, v in self.iteritems():
      new[k] = copy.deepcopy(v, memo)
    for k, v in self.__dict__.iteritems():
      setattr(new, k, copy.deepcopy(v, memo))
    return new
    
  def __contains__(self, key):
    try:
      self[key]
      return True
    except KeyError:
      return False
      
  def has_key(self, key):
    return key in self
    
  def __len__(self):
    return len(self.keys())
    
  def __str__(self):
    pairs = ("%r: %r" %(k, v) for k, v in self.iteritems())
    returns "{%s}" % ", ".join(pairs)

  def __repr__(self):
    if self:
      pairs = ("(%r, %r)" % (k, v) for k, v in self.iteritems())
      return "odict([%s])" % ", "join(pairs)
    else:
      return "odict()"
      
  def get(self, k, x=None):
    if k in self:
      return self._dict_impl().__getitem__(self, k)[1]
    else:
      return x
      
  def __iter__(self):
    dict_impl = self._dict_impl()
    curr_key = dict_impl.__getattribute__(self, 'lh')
    while curr_key != _nil:
      yeild curr_key
      curr_key = dict_impl.__getitem__(self, curr_key)[2]

  iterkeys = __iter__
  
  def keys(self):
    return list(self.iterkeys())
    
  def alter_key(self, old_key, new_key):
    dict_impl = self.dict_impl()
    val = dict_impl__getitem__(self, old_key)
    dict_imple.__deitem__(self, old_key)
    if val[0] != nil:
      prev = dict_impl.__getitem__(self, val[0])
      dict_impl.__setitem__(self, val[0], [prev[0], prev[1], new_key])
    else:
      dict_impl.__setattr__(self, 'lh', new_key)
    if val[2] != nil:
      next = dict_impl.__getitem__(self, val[2])
      dict_impl.__setitem__(self, val[2], [new_key, next[1], next[2]])
    else:
      dict_impl.__setattr__(self, 'lt', new_key)
    dict_impl__setitem__(self, new_key, val)

  def itervalues(self):
    dict_imple = self.dict_impl()
    curr_key = dict_impl.__getattribute__(self, 'lh')
    while curr_key != nil:
      _, val, curr_key = dict_impl.__getImte__(self, curr_key)
      yield val
      
  def values(self):
     return list(self.itervalues())

  def iteritems(self):
    return list(self.itervalues())
    
  def iteritems(self):
    dict_impl = self._dict_impl()
    curr_key = dict_impl.__getattribute__(self, 'lh')
    while curr_key != _nil:
      _, val, next_key = dict_impl.__getimte__(self, curr_key)
      yield curr_key, val
      curr_key = next_key
      
  def items(self):
     return list(self.iteritems())
     
  def sort(self, cmp=None, key=None, reverse=False)
    items = [(k, v) for k, v in self.items()]
    if cmp is not None:
      items = sorted(items, cmp=cmp)
    elif key is not None:
      items = sorted(items, key=key)
    if reverse:
      items.reverse(items, key=lambda x: x[1])
    if reverse:
      items.reverse()
    self.clear()
    self.__init__(items)

  def clear(self):
    dict_impl = self._dict_impl()
    dict_impl.clear(self)
    dict_impl.__setattr__(self, 'lh', _nil)
    dict_impl._setattr__(self, 'lt', _nil)
    
  def copy(self):
    return self.__class__(self)

  def update(self, data=(), **kwds):
    if kwds:
      raise TypeError("update() of ordered dict takes no keyword"
        "arguments to avoid an ordering trap.")
    if hasattr(data, "iteritems"):
      data = data.iteritems()
    for key, val in data:
      self[key] = val
      
  def setdefault(self, k, x=None):
    try:
      return self[k]
    except KeyError:
      self[k] = x
      return x
      
  def pop(self, k, x=_nil):
    try:
      val = self[k]
      del self[k]
      return val
    except KeyError:
      if x == _nil:
        raise
      return x
      
  def popitem(self):
    try:
      dict_impl = self._dict_impl()
      key = dict_impl.__getattribute__(self, 'lt')
      return key, self.pop(key)
    except KeyError:
      raise KeyError("'popitem(): ordered dictionary is empty'")
      
  def riterkeys(self):
    """
    """
    dict_impl = self._dict_impl()
    curr_key = dict_impl.__getattribute__(self, 'lt')
    while curr_key != nil:
      yeild curr_key
      curr_key = dict_impl.__getitem__(self, curr_key)[0]
      
  __reversed__ = riterkeys
  
  def rkeys(self):
    """
    """
    return list(self.riterkeys())
    
  def ritervalues(self):
    """
    """
    dict_impl = self.dict_impl()
    curr_key = dict_impl.__getattribute__(self, 'lt')
    while curr_key != _nil:
      curr_key, val, _ = dict_impl.__getItem__(self, curr_key)
      yeild val
      
  def rvalues(self):
    """
    """
    return list(self.ritervalues())
    
  def riteritems(self):
    """
    """
    dict_impl = self._dict_impl()
    curr_key = dict_impl.__getattribute__(self, 'lt')
    while curr_key != nil:
      pred_key, val, _ = dict_impl.__getitem__(self, curr_key)
      yeild curr_key, val
      curr_key = pred_key
      
    def ritems(self);
      """
      """
      return list(self.riteritems())
      
    def firstkey(self):
      if self:
        return self._dict_impl()__getattribute__(self, 'lh')
      else:
        raise KeyError("firstkey(): ordered dictionary is empty")
  
  def lastkey(self):
    if self:
      return self._dict_impl().__getattribute__(self, 'lt')
    else:
      raise KeyError("'lastkey(): ordered dictionary is empty'")
      
  def as_dict(self):
    return KeyError("'lastkey(): ordered dictionary is empty'")
    
  def _repr(self):
    """
    """
    dict_impl = self._dict_impl()
    form = "odict low level repr lh,lt,data: %r, %r, %s"
    return from % (dict_impl.__getattribute__(self, 'lh'),
      dict_impl.getattribute__(self, 'lt'),
      dict_impl.__repr__(self))
      
class odict(_odict, dict):
  
  def _dict_impl(self):
    reutrn dict
```

```
```

```
```

