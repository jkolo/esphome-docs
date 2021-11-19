Tuya Number
===========

.. seo::
    :description: Instructions for setting up a Tuya device number.
    :image: upload.svg

The ``tuya`` number platform creates a number from a tuya serial component
and requires :doc:`/components/tuya` to be configured.

.. code-block:: text

    [00:10:29][C][tuya:028]: Tuya:
    [00:10:29][C][tuya:045]:   Datapoint 101: enum (value: 6)
    [00:10:29][C][tuya:041]:   Datapoint 102: int value (value: 37)
    [00:10:29][C][tuya:047]:   Datapoint 104: bitmask (value: 0)
    [00:10:29][C][tuya:041]:   Datapoint 105: int value (value: 34)
    [00:10:29][C][tuya:045]:   Datapoint 106: enum (value: 2)
    [00:10:29][C][tuya:041]:   Datapoint 107: int value (value: 0)
    [00:10:29][C][tuya:041]:   Datapoint 108: int value (value: 5)
    [00:10:29][C][tuya:055]:   Product: '{"p":"h6MjwrnldNTu4kX3","v":"1.0.0","m":1}'

On this controller, the datapoint 102 represents the preset water temperature
setting which is what we are interested in controlling using this platform.

Based on this, you can create the number as follows:

.. code-block:: yaml

    # Create a number
    number:
    - platform: tuya
        name: Preset temperature
        number_datapoint: 102
        min_value: 35
        max_value: 100
        step: 1

Configuration variables:
------------------------

- **id** (*Optional*, :ref:`config-id`): Manually specify the ID used for code generation.
- **name** (**Required**, string): The name of the number.
- **number_datapoint** (**Required**, int): The datapoint id number of the number.
- **min_value** (**Required**, float): The minimum value this number can be.
- **max_value** (**Required**, float): The maximum value this number can be.
- **step** (**Required**, float): The granularity with which the number can be set.
- All other options from :ref:`Number <config-number>`.

See Also
--------

- :doc:`/components/number/index`
- :apiref:`tuya/number/tuya_number.h`
- :ghedit:`Edit`
