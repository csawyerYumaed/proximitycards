# proximitycards
ProximityCards algorithm for converting between diff formats.

```python
def dec_to_prox(d):
	'''
	to convert decimal # from EC API to the number on the
	proximity card. Returns a value in the form 999,99999
	'''
	h = '{:X}'.format(d)
	n1 = int(h[:2], 16)
	n2 = int(h[2:-4], 16)
	return '{},{}'.format(n1, n2)


def prox_to_dec(p):
	'''
	given a proximity card of the form 999,99999 this returns
	the decimal number required for the EC API.  The numbers
	are converted to hex {:X} and then concatenated to 101A.
	'''
	n1, n2 = p.split(',')
	return int('{:X}{:04X}101A'.format(int(n1), int(n2)), 16)
  ```
