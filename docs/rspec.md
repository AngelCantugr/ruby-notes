# Rspec

## Several ways to write tests

### One-liner syntax
Doc: https://rspec.info/features/3-12/rspec-core/subject/one-liner-syntax/

I like this syntax because it makes it easy to read. Writing theses with it is a little bit more complicated because
one has to really use the `describe` and `context` blocks, and understand how the `subject` works.

Here are some examples I have wrote in the past
```ruby
context 'contains a non-empty result field' do
  let(:result) { 'test-result' }

  it { is_expected.to eq(result) }
end
```

```ruby 
shared_examples 'matches expected userdata' do
  it { is_expected.to_not be_nil }
  it { is_expected.to_not be_empty }
  it { is_expected.to start_with '#!/bin/bash -x' }
  it { is_expected.to include(start_with 'some string') }
  it { is_expected.to include(*expected_common_userdata) unless expected_common_userdata.empty? }  # You can add conditions to the tests
  it { is_expected.to include(*expected_user_provided_userdata) unless expected_user_provided_userdata.empty? }
  it { is_expected.to include(*expected_start_service_userdata) unless expected_start_service_userdata.empty? }
  it { is_expected.to match_array expected_userdata_array }
end
```

This is a great file with plenty for examples of how to write one line tests: https://github.com/sinatra/mustermann/blob/fa22e2cf4cfdb57f452c366eac66f241827b7e9c/mustermann/spec/sinatra_spec.rb

Other ways to write one-liner tests are to not add text to the `it` block, and rely on the `subject` and context of the test.
